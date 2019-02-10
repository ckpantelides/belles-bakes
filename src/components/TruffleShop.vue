<template>
  <div>
    <hr />
    <div class="shop">
      <br />
      <h2>truffle shop</h2>
      <div class="item-container">
        <div class="item-card">
          <p>milk chocolate</p>
          <img class="item-pic" src="../assets/truffles.jpg" />
          <p class="item-blurb">smooth, rich truffles</p>
          <p class="item-blurb">that will melt in your mouth</p>
          <br />
          <p class="item-blurb" style="font-style:italic">£10.00 per box</p>
          <p class="item-blurb" style="font-style:italic">of 10 truffles</p>
          <button class="cart-add" @click="cartMinus(milkChocTruffle)">
            -
          </button>
          <span style="font-size:0.8rem">{{ milkChocTruffle.cart }}</span>
          <button class="cart-add" @click="cartAdd(milkChocTruffle)">+</button>
          <br />
          <button class="cart-send" @click="sendToCheckout(milkChocTruffle)">
            add to cart
          </button>
          <p class="item-blurb" v-if="milkChocTruffle.cart > 0">
            £{{ subTotal(milkChocTruffle) }}
          </p>
        </div>
        <div class="item-card">
          <p>dark chocolate</p>
          <img class="item-pic" src="../assets/truffles.jpg" />
          <p class="item-blurb">smooth, rich truffles</p>
          <p class="item-blurb">that will melt in your mouth</p>
          <br />
          <p class="item-blurb" style="font-style:italic">£12.00 per box</p>
          <p class="item-blurb" style="font-style:italic">of 10 truffles</p>
          <button class="cart-add" @click="cartMinus(darkChocTruffle)">
            -
          </button>
          <span style="font-size:0.8rem">{{ darkChocTruffle.cart }}</span>
          <button class="cart-add" @click="cartAdd(darkChocTruffle)">+</button>
          <br />
          <button class="cart-send" @click="sendToCheckout(darkChocTruffle)">
            add to cart
          </button>
          <p class="item-blurb" v-if="darkChocTruffle.cart > 0">
            £{{ subTotal(darkChocTruffle) }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TruffleShop',
  props: {},
  data: function() {
    return {
      id: -1,
      milkChocTruffle: {
        name: 'milk chocolate truffles',
        cart: 0,
        price: 0,
        unitPrice: 10,
        id: 0
      },
      darkChocTruffle: {
        name: 'dark chocolate truffles',
        cart: 0,
        price: 0,
        unitPrice: 12,
        id: 0
      }
    }
  },
  methods: {
    cartAdd(product) {
      if (product.cart < 5) {
        product.cart += 1
      }
    },
    cartMinus(product) {
      if (product.cart > 0) {
        product.cart -= 1
      }
    },
    subTotal(product) {
      if (product.cart > 0) {
        product.price = (product.cart * product.unitPrice).toFixed(2)
        return product.price
      }
    },
    sendToCheckout(product) {
      this.id += 1
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
  height: 470px;
  margin-left: 10rem;
  margin-right: 10rem;
  /*
  border: solid 1px #58381e;
   padding: 15px;
  margin: 20px;
  */
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
}

p.item-blurb {
  font-size: 0.75rem;
  margin: 0rem;
}

.item-container {
  display: flex;
}

.item-card {
  flex: 1;
}

.item-pic {
  height: 200px;
  width: 200px;
}

button {
  font-size: 0.7rem;
  display: inline;
  font-family: 'Comfortaa', cursive;
}

button.cart-add {
  background-color: white;
  border: none;
}

button.cart-send {
  background-color: white;
  border: solid 1px #331d0b;
}
</style>
