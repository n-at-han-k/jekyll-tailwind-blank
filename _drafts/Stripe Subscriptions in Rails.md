---
title: Stripe Subscriptions in Rails
layout: post
---
The Plans API is the old way of managing subscriptions. The Prices API is the new way.
https://stripe.com/docs/api/prices

They have a handy guide for setting up a subscription
https://stripe.com/docs/billing/subscriptions/build-subscriptions

Other links here:
https://stripe.com/docs/billing/subscriptions/overview#subscription-events
https://stripe.com/docs/billing/subscriptions/webhooks


You should create a `POST` route to create a checkout session `/create-checkout-session` which takes a `priceId` parameter.

This can be done with `button_to` or any other kind of form.
```ruby
<%= button_to ‘Choose plan’, stripe_checkout_session_path,
              method: :post, params: {price_id: ‘8093485jaskdfjfdsf’} %>
```

The controller should create a stripe checkout session and redirect the client.
```ruby
session = Stripe::Checkout::Session.create({
   customer_reference_id: tenant_id,
   customer: stripe_customer_id,
   success_url: '',
   cancel_url: '',
   mode: 'subscription',
   line_items: [{
      # For metered billing, do not pass quantity
      quantity: 1,
      price: price_id,
   }],
})
redirect_to session.url

```

Possible values for subscription status are `incomplete`, `incomplete_expired`, `trialing`, `active`, `past_due`, `canceled`, or `unpaid`.