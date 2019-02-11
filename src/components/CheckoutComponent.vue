<template>
  <div>
    <!--
    <hr />
    -->
    <div class="shop">
      <br />
      <!--
      <h2>checkout</h2>
      -->
      <div v-if="baskets.length < 1">
        <img src="../assets/emptyBasket2.jpg" />
      </div>
      <div v-else-if="baskets.length > 0">
        <div class="checkout-wrapper">
          <div class="order-container">
            <br />
            <p style="text-decoration:underline">
              <b>your order</b>
            </p>
            <br />
            <table class="checkout">
              <th>type</th>
              <th>boxes</th>
              <th>price</th>
              <td style="font-size:0.75rem; font-style:italic">remove</td>

              <tr v-for="(basket, index) in baskets" :key="basket.id">
                <td>{{ basket.name }}</td>
                <td>{{ basket.cart }}</td>
                <td>£{{ basket.price }}</td>
                <button class="delete" @click="removeItem(index)">-</button>
              </tr>
              <tr>
                &nbsp;
              </tr>
              <th>total</th>
              <th>{{ totalBoxes }}</th>
              <th>£{{ grandTotal }}</th>
              <tr>
                &nbsp;
              </tr>
            </table>

            <br />
            <br />
            <div v-if="totalBoxes > 0 && totalBoxes < 6">
              <table class="checkout">
                <th>shipping</th>
                <th>&nbsp;&nbsp;&nbsp;</th>
                <th>£{{ shipping }}</th>
                <th>&nbsp;&nbsp;&nbsp;</th>
                <tr></tr>
                <th>all in</th>
                <th>&nbsp;&nbsp;&nbsp;</th>
                <th style="border:1px solid">£{{ costWithShipping }}</th>
                <th>&nbsp;&nbsp;&nbsp;</th>
              </table>

              <br />
              <button class="pay">Pay now</button>
            </div>

            <div v-else-if="totalBoxes >= 6">
              <p>
                We can only accept orders of 5 boxes or less at the moment.
                Please delete some items from your basket
              </p>
            </div>
          </div>
          <div class="order-container">
            <br />
            <p style="text-decoration:underline">
              <b>your details</b>
            </p>
            <br />
            <p>name</p>
            <p>address</p>

            <br />
            <br />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CheckoutComponent',
  props: {
    baskets: Array
  },
  data: function() {
    return {}
  },
  methods: {
    removeItem(data) {
      //  this.baskets.splice(item, 1)
      this.baskets.splice(data, 1)
      // this.$delete(this.baskets, basket.id)
      this.$emit('update-cart-number', this.totalBoxes)
    }
  },
  computed: {
    grandTotal() {
      // reduce method is used to add the prices in the baskets array
      let totalFloat = this.baskets.reduce(
        (acc, item) => acc + parseFloat(item.price, 0),
        0
      )
      return totalFloat.toFixed(2)
    },
    totalBoxes() {
      return this.baskets.reduce((acc, item) => acc + parseInt(item.cart, 0), 0)
    },
    shipping() {
      if (this.totalBoxes < 2) return parseFloat(2).toFixed(2)
      else return parseFloat(4).toFixed(2)
    },
    costWithShipping() {
      return (parseFloat(this.grandTotal) + parseFloat(this.shipping)).toFixed(
        2
      )
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url('https://fonts.googleapis.com/css?family=Comfortaa');

div.shop {
  clear: both;
  display: block;
  height: 526px;
  margin-top: 20px;
  background: #af7e58;
}

.checkout-wrapper {
  display: flex;
  width: 90%;
  margin-left: auto;
  margin-right: auto;
}

.order-container {
  flex: 1;
  width: 40%;
  margin-right: auto;
  margin-left: auto;
  background: white;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.8);
  height: 480px;
  padding: 2px 10px;
  margin: 0% 2%;
}

hr {
  display: block;
  width: 100%;
  margin-top: -10px;
  margin-bottom: -25px;
  border-style: solid;
  border-width: 1px;
  color: #331d0b;
}

h2 {
  font-family: 'Comfortaa', cursive;
  font-size: 2rem;
  font-weight: 200;
  color: #58381e;
  margin-top: 25px;
}

p {
  margin-top: -20px;
  color: #331d0b;
  font-size: 1rem;
}

p.question {
  font-weight: bold;
}

table.checkout {
  font-size: 0.95rem;
  width: 95%;
  margin-left: auto;
  margin-right: auto;
}

button.delete {
  background-color: white;
  border: none;
}

button.pay {
  background-color: white;
  color: #331d0b;
  font-family: 'Comfortaa', cursive;
  font-size: 1.25rem;
  border: 1px #331d0b solid;
}

img {
  width: 100%;
  height: 529px;
  object-fit: cover;
  margin-top: -30px;
  margin-bottom: 0px;
}
</style>
