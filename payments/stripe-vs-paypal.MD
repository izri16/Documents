## Stripe
* complete payment system, suited for developers with a lof of customization options
* also includes default payment form for quick prototyping
* you can set up your own server, customize payment form and register "webhook" to listen
   when payment is complete, in general you can have a lot of control over payments using stripe sdk
* currently support receiving payments in less countries than Paypal but the support is growing

## Paypal
* payment system where you can create account, link debit/credit card to it and pay using that
   account on web, or send money to another paypal users using just their email
* you can pay by paypal option even when you do not have the paypal account, you should be
   redirected to "credit card" option
* should offer an easier integration for non-tech people, but with much less customization
   than stripe
* offers *braintree* which is a tool similar stripe


In both stripe and paypal you pay a percentage from transaction (around 2.9% + 30cents).

