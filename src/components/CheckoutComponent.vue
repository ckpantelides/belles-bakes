<template>
  <div>
    <div class="shop">
      <hr />
      <div v-if="baskets.length < 1">
        <br />
        <img src="../assets/emptyBasket2.jpg" />
      </div>
      <div v-else-if="baskets.length > 0">
        <div class="checkout-wrapper">
          <div class="order-container">
            <p style="text-decoration:underline">
              <b>your details</b>
            </p>
            <br />
            <p>name</p>
            <p>address</p>

            <br />
            <br />
          </div>
          <div class="order-container">
            <br />
            <p style="text-decoration:underline">
              <b>your order</b>
            </p>
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
                <th style="text-decoration:underline">
                  £{{ costWithShipping }}
                </th>
                <th>&nbsp;&nbsp;&nbsp;</th>
              </table>

              <br />
              <button class="pay">place order</button>
            </div>

            <div v-else-if="totalBoxes >= 6">
              <p>
                We can only accept orders of 5 boxes or less at the moment.
                Please delete some items from your basket
              </p>
            </div>
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
  height: 82vh;
  background: #faf2ed;
}

img {
  width: 100vw;
  height: 83vh;
  object-fit: cover;
  margin: 0;
  margin-top: -28px;
}

hr {
  display: none;
  width: 100%;
  border-style: solid;
  border-width: 4px;
  color: #faf2ed;
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
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.4);
  height: 480px;
  padding: 2px 10px;
  margin: 0% 2%;
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
  border: none;
  text-decoration: underline;
}

@media screen and (max-width: 600px) {
  .header {
    height: 13vh;
  }
  div.shop {
    background: white;
  }

  hr {
    display: block;
    margin-top: -10px;
  }

  img {
    margin-top: -40px;
    height: 90vh;
  }

  .checkout-wrapper {
    display: flex;
    width: 90%;
    margin-left: auto;
    margin-right: auto;
    flex-wrap: nowrap;
    flex-direction: column;
  }

  .order-container {
    justify-content: center;
    width: 90%;
    height: auto;
    box-shadow: none;
  }
}
</style>
