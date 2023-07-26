---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Definition of Parameters in the output of Data Feed

To use data feed function, merchant has to create a data feed page and inform PayDollar about the location of your page (e.g. http://www.yourdomain.com/datafeed.jsp). Merchant can enable or disable this function in the merchant administration site.



| Parameters  | Data Type     | Descriptions                                                                     |
| ----------- | ------------- | -------------------------------------------------------------------------------- |
| src         | Text          | Return bank host status code (secondary). Please refer to Appendix A for detail. |
| prc         | Text          | Return bank host status code (primary). Please refer to Appendix A for detail.   |
| Ord         | Text (40)     | Bank Reference Number                                                            |
| Holder      | Text          | The Holder Name of the Payment Account                                           |
| successcode | Number        | 0- succeeded, 1- failure, Others - error                                         |
| Ref         | Text          | Merchant‘s Order Reference Number                                                |
| PayRef      | Number        | PayDollar Payment Reference Number                                               |
| Amt         | Number (12,2) | Transaction Amount                                                               |

The data feed page must meet the following requirement:

* Print ‘OK’ in HTML when data captured (ACK message)
* Make Sure to Print ‘OK’ for acknowledge to our system first then do the rest of your system process, if something wrong with your system process (i.e. download photo, ring tone problem) you can send a void request to our system, for more details please refer to our API guide and contact our technical staff. PayDollar PayGate Integration Guide (v3.66) Page 68 Please note that the system only supports either port 80 (HTTP) or 443 (HTTPS) for the data feed page location. And make sure the data feed page location is externally accessible, so that our server can call the data feed page.
* Since the system will read from the data feed page for the word ‘OK’ to determine whether the (data feed) message is delivered or not, if this word does not return successfully, the system will assume the data feed is lost.



**Sample Data Feed Page**

The following is a sample data feed page in JSP.

```
<%@ page language="java" %>
<%
 String successCode = request.getParameter("successcode");
 String payRef = request.getParameter("PayRef");
 String Ref = request.getParameter("Ref");
 // Print out 'OK' to notify us you have received the payment result
 out.print("OK");
 if ( successCode.equals("0") )
 {
 // Transaction Accepted
 // *** Add the Security Control here, to check the currency, amount with
the
 // *** merchant’s order reference from your database, if the order exist
then
 // *** accepted otherwise rejected the transaction.
 // Update your database for Transaction Accepted and send email or notify
your
 // customer.
 ....
// In case if your database or your system got problem, you can send a
void transaction request. See API guide for more details
 }
 else
 {
 // Transaction Rejected
 // Update your database for Transaction Rejected
 .....
 }
%>
```

The following is a sample data feed page in ASP.

```
<%@ Language = "VBScript" %>
<%
 Dim successCode
 Dim payRef
 Dim Ref

 successCode = Request.Form("successcode")
 payRef = Request.Form("PayRef")
 Ref = Request.Form("Ref")
' Print out 'OK' to notify us you have received the payment result
 Response.write("OK")
 If successCode = "0" Then
 ' Transaction Accepted
 ' *** Add the Security Control here, to check the currency, amount with the
 ' *** merchant’s order reference from your database, if the order exist then
 ' *** accepted otherwise rejected the transaction.
 ' Update your database for Transaction Accepted and send email or notify your
 ' customer.
 .....
 ' In case if your database or your system got problem, you can send a void
 ' transaction request. See API guide for more details
 Else
 ' Transaction Rejected
 ' Update your database for Transaction Rejected
 .....
 End If
%>
```

