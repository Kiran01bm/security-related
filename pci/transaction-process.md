## General Transaction Process

When a customer orders a product from a payment gateway-enabled **merchant**, the **payment gateway** performs a variety of tasks to process the transaction.

1. A customer places an order on website by pressing the 'Submit Order' or equivalent button, or perhaps enters their card details using an automatic phone answering service.
2. If the order is via a website, the customer's web browser encrypts the information to be sent between the browser and the merchant's webserver. In between other methods, this may be done via SSL (Secure Socket Layer) encryption. The payment gateway may allow transaction data to be sent directly from the customer's browser to the gateway, bypassing the merchant's systems. This reduces the merchant's Payment Card Industry Data Security Standard (PCI DSS) compliance obligations without redirecting the customer away from the website.
3. The merchant then forwards the transaction details to their payment gateway. This is another (SSL) encrypted connection to the payment server hosted by the payment gateway.
4. The payment gateway converts the message from XML to ISO 8583 or a variant message format (format understood by EFT Switches) and then forwards the transaction information to the **payment processor** used by the **merchant's acquiring bank.**
5. The payment processor forwards the transaction information to the **card association** (I.e.: Visa/MasterCard/American Express). If an American Express or Discover Card was used, then the card association also acts as the issuing bank and directly provides a response of approved or declined to the payment gateway. Otherwise [e.g.: MasterCard or Visa card was used], the card association routes the transaction to the correct card **issuing bank**.
6. The credit card issuing bank receives the authorization request, verifies the credit or debit available and then sends a response back to the processor (via the same process as the request for authorization) with a response code (I.e.:: approved, denied). In addition to communicating the fate of the authorization request, the response code is also used to define the reason why the transaction failed (I.e.: insufficient funds, or bank link not available). Meanwhile, the credit card issuer holds an authorization associated with that merchant and consumer for the approved amount. This can impact the consumer's ability to spend further (because it reduces the line of credit available or it puts a hold on a portion of the funds in a debit account).
7. The processor forwards the authorization response to the payment gateway.
8. The payment gateway receives the response, and forwards it onto the website, or whatever interface was used to process the payment, where it is interpreted as a relevant response, then relayed back to the merchant and cardholder. This is known as the Authorization or "Auth."
9. The entire process typically takes 2–3 seconds.
10. The merchant then fulfills the order and the above process can be repeated but this time to "Clear" the authorization by consummating the transaction. Typically, the "Clear" is initiated only after the merchant has fulfilled the transaction (I.e. shipped the order). This results in the issuing bank 'clearing' the 'auth' (I.e. moves auth-hold to a debit) and prepares them to settle with the merchant acquiring bank.
11. The merchant submits all their approved authorizations, in a "batch" (end of the day), to their acquiring bank for settlement via its processor. This typically reduces or "Clears" the corresponding "Auth" if it has not been explicitly "Cleared."
12. The acquiring bank makes the batch settlement request of the credit card issuer.
13. The credit card issuer makes a settlement payment to the acquiring bank (the next day in most cases).
14. The acquiring bank subsequently deposits the total of the approved funds into the merchant's nominated account (the same day or next day). This could be an account with the acquiring bank if the merchant does their banking with the same bank, or an account with another bank.
15. The entire process from authorization to settlement to funding typically takes 3 days.

**Note** Many payment gateways also provide tools to automatically screen orders for fraud and calculate tax in real time prior to the authorization request being sent to the processor. Tools to detect fraud include geolocation, velocity pattern analysis, OFAC list lookups, 'black-list' lookups, delivery address verification, computer finger printing technology, identity morphing detection, and basic AVS checks.


