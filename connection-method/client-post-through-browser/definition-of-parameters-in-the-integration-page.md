# Definition of Parameters in the Integration Page

The following are the parameters for integration. PayDollar PayGate is case sensitive. Make sure the typeface is correct. When a transaction is finished, the system will return customer a payment message. Merchant can create static HTML pages to display the message. If merchant’s web site supports data feed, the system can return payment message as shown in the following table.

| Parameters | Data Type     | Descriptions                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| ---------- | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| orderRef   | Text (35)     | Merchant‘s Order Reference Number                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| currCode   | Text (3)      | <p>The currency of the payment: </p><p>“344” – HKD           “840” – USD     “702” – SGD “156” – CNY (RMB) “392” – JPY     “901” – TWD “036” – AUD            “978” – EUR     “826” – GBP “124” – CAD             “446” – MOP   “608” – PHP “764” – THB             “458” – MYR   “360” – IDR “410” – KRW             “682” – SAR    “554” – NZD “784” – AED             “096” – BND    “704” – VND “356” – INR </p><p>Remark: </p><p>mpsMode = SCP, the currCode value should be in foreign currency. </p><p>mpsMode = MCP, the currCode value should be in base currency.</p> |
| amount     | Number (12,2) | <p>The total amount you want to charge the customer for the provided currency.</p><p>Remark: </p><p>mpsMode = SCP, the amount should be calculated in foreign currency. </p><p>mpsMode = MCP, the amount should be calculated in base currency.</p>                                                                                                                                                                                                                                                                                                                             |



<mark style="color:orange;">**Example of Client Post Method (Source Code)**</mark>

The following is an example of integration of shopping cart routine with the payment routine of PayDollar PayGate in HTML. It is noteworthy that the portion in bold typeface as follows is mandatory for successful integration.

In the following sample form, hidden fields are used to hold the values:

```
// <form name="payFormCcard" method="post" action="
https://test.paydollar.com/b2cDemo/eng/payment/payForm.jsp">
<input type="hidden" name="merchantId" value="1">
<input type="hidden" name="amount" value="3000" >
<input type="hidden" name="orderRef" value="000000000014">
<input type="hidden" name="currCode" value="344" >
<input type="hidden" name="mpsMode" value="NIL" >
<input type="hidden" name="successUrl"
value="http://www.yourdomain.com/Success.html">
<input type="hidden" name="failUrl" value="http://www.yourdomain.com/Fail.html">
<input type="hidden" name="cancelUrl"
value="http://www.yourdomain.com/Cancel.html">
<input type="hidden" name="payType" value="N">
<input type="hidden" name="lang" value="E">
<input type="hidden" name="payMethod" value="CC">
<input type="hidden" name="secureHash"
value="44f3760c201d3688440f62497736bfa2aadd1bc0">
<input type="submit" name="submit">
</form>
```

### <mark style="color:orange;">Kick Off</mark> &#x20;

After the integration has been completed, it is ready to launch your e-commerce web to serve your customers. Please copy the following TESTING URL for client post method:

{% code fullWidth="true" %}
```
https://test.paydollar.com/b2cDemo/eng/payment/payForm.jsp
```
{% endcode %}
