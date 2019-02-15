<template>
  <div>
    <div class="shop">
      <hr />
      <br />
      <div class="subscription-container">
        <p class="question">The perfect gift for you and your loved ones</p>
        <p>We offer quarterly, six-monthly and yearly subscriptions</p>
        <p>
          Our subscription requires just one payment. The lucky recipient will
          receive one full batch (8 pieces) every month, with a different
          flavour each time. We’ll send the first box with a card on a date of
          your choice. We’ll also send them an email telling them the dates
          they’ll be receiving their next boxes so they can contact us to change
          it if they need to – don’t worry we won’t send this until they’ve
          signed for their first box!
        </p>
        <br />
        <div class="subscription" @click="sendToCheckout(quarterlySub)">
          <p style="font-weight:bold">Quarterly subscription</p>
          <p>(1 box of brownies each month for three months)</p>
          <p style="font-weight:bold">£30</p>
        </div>
        <br />
        <div class="subscription" @click="sendToCheckout(sixMonthSub)">
          <p style="font-weight:bold">Six month subscription</p>
          <p>(1 box of brownies each month for six months)</p>
          <p style="font-weight:bold">£50</p>
        </div>
        <br />
        <div class="subscription" @click="sendToCheckout(yearlySub)">
          <p style="font-weight:bold">Full year subscription</p>
          <p>(1 box of brownies each month for twelve months)</p>
          <p style="font-weight:bold">£90</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Subscription',
  props: {},
  data: function() {
    return {
      id: 30,
      quarterlySub: {
        name: 'quarterly subscription',
        cart: 1,
        price: 30,
        id: 0
      },
      sixMonthSub: {
        name: 'six month subscription',
        cart: 1,
        price: 50,
        id: 0
      },
      yearlySub: {
        name: 'one year subscription',
        cart: 1,
        price: 90,
        id: 0
      }
    }
  },
  methods: {
    sendToCheckout(product) {
      this.id++
      product.id = this.id
      this.$emit('send-to-checkout', product)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div.shop {
  clear: both;
  display: block;
  height: 82vh;
  background: #faf2ed;
}

hr {
  display: none;
  width: 100%;
  margin-top: -10px;
  border-style: solid;
  border-width: 4px;
  color: #faf2ed;
}

.subscription-container {
  width: 75%;
  margin-right: auto;
  margin-left: auto;
  background: white;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.8);
  height: 480px;
  padding: 2px 10px;
}

h2 {
  font-family: 'Comfortaa', cursive;
  font-size: 2rem;
  font-weight: 200;
  color: #58381e;
  margin-top: 25px;
}

p {
  color: #331d0b;
  font-size: 0.8rem;
}

p.question {
  font-weight: bold;
}

div.subscription {
  border: solid 1px;
  width: 40%;
  margin-left: auto;
  margin-right: auto;
  cursor: pointer;
  padding: 2px;
}

div.subscription p {
  margin: 0;
  padding: 0;
}

@media screen and (max-width: 600px) {
  .header {
    height: 13vh;
  }
  div.shop {
    background: white;
    overflow-y: scroll;
    margin-top: -15px;
  }

  hr {
    display: block;
    margin-top: 0;
  }

  .subscription-container {
    width: 90%;
    margin-left: auto;
    margin-right: auto;
    height: auto;
    box-shadow: none;
  }

  div.subscription {
    width: 100%;
  }
}
</style>
