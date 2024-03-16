
The Plans API is the old way of managing subscriptions. The Prices API is the new way.
https://stripe.com/docs/api/prices

They have a handy guide for setting up a subscription
https://stripe.com/docs/billing/subscriptions/build-subscriptions

You should create a `POST` route to create a checkout session `/create-checkout-session` which takes a `priceId` parameter.
