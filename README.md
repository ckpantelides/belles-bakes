Belle's Bakes storefront
=================

It's hosted [here](https://ckpantelides.github.io/belles-bakes)
The backend code is [here](https://github.com/ckpantelides/belles-server)

#### A storefront built with Vue

A single page app built with components (for the brownie shop, truffle shop, checkout etc). There's a cart that updates as orders are added to it, and Stripe is integrated for payments. The order details are sent via axios to the backend, which authorises the payments and sends email receipts.

Make a test payment using the credit card number: 4242 4242 4242 4242.

![img1] ![img2]

[img1]: https://github.com/ckpantelides/node-weather/blob/images/weather1.jpg
[img2]: https://github.com/ckpantelides/node-weather/blob/images/weather2.png

#### Installation

> npm install

> npm run serve (compiles for development)

> npm run build (compiles for production)
