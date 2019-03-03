<template>
  <div>
    <vue-stripe-checkout
      ref="checkoutRef"
      :amount="fixedAmount"
      billing-address="true"
      shipping-address="true"
      zip-code="true"
      :image="image"
      :description="description"
      :currency="currency"
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
import axios from 'axios'
Vue.use(VueStripeCheckout, 'pk_test_CLqR7AIwqCkJdz1hwqIX8cpy')

export default {
  props: {
    amount: Number,
    baskets: Array
  },
  data() {
    return {
      image: require('../assets/schnauzer.jpg'),
      description: 'Thank you for your order',
      currency: 'gbp'
    }
  },
  methods: {
    async checkout() {
      const { token, args } = await this.$refs.checkoutRef.open()
    },
    done({ token, args }) {
      // token - is the token object
      // args - is an object containing the billing and shipping address if enabled
      const price = this.amount
      const baskets = this.baskets
      // post(`http://localhost:5400/post`
      // `https://belles-server.herokuapp.com/post`
      axios
        .post(`https://belles-server.herokuapp.com/post`, {
          body: { token, args, price, baskets }
        })
        .then(response => {})
        .catch(e => {
          this.errors.push(e)
        })
      this.$emit('thank-you')
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
  },
  computed: {
    fixedAmount() {
      return parseFloat(this.amount)
    }
  }
}
</script>

<style scoped>
button {
  background-color: white;
  color: #331d0b;
  font-family: 'Comfortaa', cursive;
  font-size: 1.25rem;
  border: none;
  text-decoration: underline;
}
</style>
