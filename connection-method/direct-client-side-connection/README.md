# Direct Client Side Connection

This method is used for the merchant if they want to capture the credit card information from their web page instead of using our standard payment page. The requirement of using this method is to install a SSL Certificate to your domain in order to protect your customers’ credit card information.&#x20;

Moreover, if the credit card used by the customer is an enrolled 3-D Secure card, the customer will be asked for providing a static password or one-time password to verify the payer identity. 3-D Secure is a credit card authorization program implemented by VISA with brand named “Verified By VISA”, MasterCard with brand named “MasterCard SecureCode”, JCB with brand named “J/Secure” and AMEX with brand named “AMEX SafeKey” to reduce fraudulent purchases by verifying purchaser identity during online transactions. PayDollar will assist to carry out this process and the customer will observe the 3D processing pages by our PayDollar shown as the later section.&#x20;

As the 3D protocol is standardized for all brand types, including Verified By VISA, MasterCard SecureCode, JCB J/Secure and AMEX SafeKey. In this document, we use the case of Verified By VISA as an example to show the flow in detail.&#x20;

For merchant who chooses this method of connection, 128-bit SSL sever certificate must be installed for data encryption. The system does not accept non-encrypted data.

PayDollar use Extended Validation (EV) SSL Certificate to ensure your system function properly, please check your certificate store can recognize VeriSign intermediate CA certificate - Secure Site Pro/Managed PKI for SSL Premium with EV Certificates. If not, you are required to install the VeriSign intermediate CA certificate in your certificate store.&#x20;

Please download the primary and secondary VeriSign EV SSL Intermediate CA certificates from the following link then import the 2 certificates into the keystore of your environment.&#x20;

http://www.verisign.com/support/verisign-intermediate-ca/extended-validation-pro/index.html&#x20;

(Please be reminded that you should choose the option “Issued After May 17th, 2009”)
