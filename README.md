Payumoney Documentation :
=========================

=> Payumoney offers electronic payment service to your website through its various  patnerships with banks.

=> Through payumoney your client would be able to make electronic payments through credit card or net banking or debit cart.

=> Payumoney also offers to merchent(owner of website) for online transection detatils, settlement reports,analytic reports etc

=> There is two types of login is provided by payumoney one for buyer and another one is merchent


Payumoney payment process like below :
=====================================
  
  ->  The consumer select the product on your website and cliks on "pay now" button 
  ->  The consumer get the transection page of payumoney.here consumer will enter all   payment related detatils
  ->  Payu send the cusumer details and account details to the right bank.
  ->  The bank varifies the consumere tell wethere the transection is success or failure 
  ->  Payu pass the customer back to merchent website along with the confirmation whether the transection is fail or success
  ->  Merchent shows a success or failure messsage to consumer.


Payuindia gem and form :
========================

gem 'payuindia'

-> we have to put this form where into where you wnat like cart page

<% payment_form_for_payu 'gtKFFx', 'eCwWELxi',
      :txnid => "84t3#te3gdeg578",
      :amount => 50,
      :productinfo => 'Mobile',
      :firstname => 'abc',
      :email => 'p.maheshvarma18@gmail.com',
      :phone => '1234567890',
      :surl => 'http://localhost:3000/continue',
      :furl => 'http://localhost:3000/continue',
      :html => { :id => 'payment-form' } %>'

-> txnid should be alphanumeric
-> payment_form_for_payu is inbuilt helper method provided by payuindia gem

params required for post form :
================================

The parameters to post are described below:

-> Key - mandotary
-> Salt - mandotary
-> amount - mandotary
-> productinfo - mandotary
-> firstname - mandotary
-> email - mandotary
-> phone - mandotary
-> surl - mandotary(Success URL where PayUMoney will redirect after successful payment.)
-> furl - mandotary(Failure URL where PayUMoney will redirect after failed payment.)
-> curl - Cancel URL where PayUMoney will redirect when user cancel the transaction.
-> hash(Checksum) - mandotary(Hash or Checksum =sha512(key|txnid|amount|productinfo|firstname|email|udf1|udf2|udf3|udf4|udf5||||||salt))
-> service_provider-Compulsory(payu_paisa)

Technical Integration :
=======================

-> The payment process flow to move the consumer from step1(click on pay now) to step 2(getting PayUMoney page from payu) post request generated need by merchent to following given url
->  Production server:
    POST URL: https://secure.payu.in/_payment
->  Test server:
    POSL URL: https://test.payu.in/_payment


Test credentials :
==================

Test Key – JBZaLc
Test Salt – GQs7yium
Test Card Name: any name
Test Card Number: 5123456789012346
Test CVV: 123
Test Expiry: May 2017

-> we have to register test.payumoney.com with buyer account and you have to give this credentials on the transection time.
-> Commint to merchant account the will give test credentials for testing purpose.but comming to production we have to registe then we will get merchantId and key_id and slat_id on setting of your dashboard. 

Responce status :
=================

There is different types of responses status given by Payumoney

->  Not started - The transection is not started yet
->  Initiated - The transaction has been started but not completed.
->  Refunded - The transection amount is Refunded
->  Partially Refunded - The partiall amount Refunded
->  Failed - The transection is failed
->  Completed - The transection is successfully completed


References URLs
================

https://www.payumoney.com/faq_details.html?topic=contact_us
http://acao.in/wp-content/uploads/bsk-pdf-manager/1_INTEGRATION_DOCUMENT_VERSION_2.5.PDF
http://stackoverflow.com/questions/31681781/payumoney-getway-error-occur-in-ios
https://www.payumoney.com/websiteintegration.html
http://developers.payu.com/en/restapi.html#references_form_signature
https://blog.payu.in/?p=206
https://blog.payumoney.com/?p=55