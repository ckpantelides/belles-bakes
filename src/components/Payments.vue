<template>
  <div>
    <vue-stripe-checkout
      ref="checkoutRef"
      :image="image"
      :name="name"
      :description="description"
      :currency="currency"
      :amount="amount"
      :allow-remember-me="false"
      @done="done"
      @opened="opened"
      @closed="closed"
      @canceled="canceled"
    ></vue-stripe-checkout>
    <button @click="checkout">place order</button>
  </div>
</template>

<script>
import Vue from 'vue'
import VueStripeCheckout from 'vue-stripe-checkout'

Vue.use(VueStripeCheckout, 'your-publishable-key-here')

export default {
  data() {
    return {
      image: 'https://i.imgur.com/HhqxVCW.jpg',
      name: 'Shut up and take my money!',
      description: 'Thank you for your order',
      currency: '£',
      amount: 99999
    }
  },
  methods: {
    async checkout() {
      // token - is the token object
      // args - is an object containing the billing and shipping address if enabled
      const { token, args } = await this.$refs.checkoutRef.open()
    },
    done({ token, args }) {
      // token - is the token object
      // args - is an object containing the billing and shipping address if enabled
      // do stuff...
    },
    opened() {
      // do stuff
    },
    closed() {
      // do stuff
    },
    canceled() {
      // do stuff
    }
  }
}
</script>
