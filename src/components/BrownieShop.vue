<template>
  <div>
    <hr />
    <div class="shop">
      <br />
      <h2>brownie shop</h2>
      <div class="item-container">
        <div class="item-card">
          <p>classic</p>
          <img class="item-pic" src="../assets/brownies.jpg" />
          <p class="item-blurb">smooth, rich milk chocolate brownies</p>
          <p class="item-blurb">that will melt in your mouth</p>
          <br />
          <p class="item-blurb" style="font-style:italic">£12.00 per box</p>
          <p class="item-blurb" style="font-style:italic">of 8 brownies</p>
          <button class="cart-add" @click="cartMinus(classicBrownie)">-</button>
          <span style="font-size:0.8rem">{{ classicBrownie.cart }}</span>
          <button class="cart-add" @click="cartAdd(classicBrownie)">+</button>
          <br />
          <button class="cart-send" @click="sendToCheckout(classicBrownie)">
            add to cart
          </button>
          <p class="item-blurb" v-if="classicBrownie.cart > 0">
            £{{ subTotal(classicBrownie) }}
          </p>
        </div>
        <div class="item-card">
          <p>dark chocolate & sea salt</p>
          <img class="item-pic" src="../assets/brownies.jpg" />
          <p class="item-blurb">smooth, rich brownies</p>
          <p class="item-blurb">that will melt in your mouth</p>
          <br />
          <p class="item-blurb" style="font-style:italic">£13.00 per box</p>
          <p class="item-blurb" style="font-style:italic">of 8 brownies</p>
          <button class="cart-add" @click="cartMinus(darkChocBrownie)">
            -
          </button>
          <span style="font-size:0.8rem">{{ darkChocBrownie.cart }}</span>
          <button class="cart-add" @click="cartAdd(darkChocBrownie)">+</button>
          <br />
          <button class="cart-send" @click="sendToCheckout(darkChocBrownie)">
            add to cart
          </button>
          <p class="item-blurb" v-if="darkChocBrownie.cart > 0">
            £{{ subTotal(darkChocBrownie) }}
          </p>
        </div>
        <div class="item-card">
          <p>salted caramel</p>
          <img class="item-pic" src="../assets/brownies.jpg" />
          <p class="item-blurb">smooth, rich brownies</p>
          <p class="item-blurb">that will melt in your mouth</p>
          <br />
          <p class="item-blurb" style="font-style:italic">£12.50 per box</p>
          <p class="item-blurb" style="font-style:italic">of 8 brownies</p>
          <button class="cart-add" @click="cartMinus(caramelBrownie)">-</button>
          <span style="font-size:0.8rem">{{ caramelBrownie.cart }}</span>
          <button class="cart-add" @click="cartAdd(caramelBrownie)">+</button>
          <br />
          <button class="cart-send" @click="sendToCheckout(caramelBrownie)">
            add to cart
          </button>
          <p class="item-blurb" v-if="caramelBrownie.cart > 0">
            £{{ subTotal(caramelBrownie) }}
          </p>
        </div>
        <div class="item-card">
          <p>fudge</p>
          <img class="item-pic" src="../assets/brownies.jpg" />
          <p class="item-blurb">smooth, rich brownies</p>
          <p class="item-blurb">that will melt in your mouth</p>
          <br />
          <p class="item-blurb" style="font-style:italic">£12.50 per box</p>
          <p class="item-blurb" style="font-style:italic">of 8 brownies</p>
          <button class="cart-add" @click="cartMinus(fudgeBrownie)">-</button>
          <span style="font-size:0.8rem">{{ fudgeBrownie.cart }}</span>
          <button class="cart-add" @click="cartAdd(fudgeBrownie)">+</button>
          <br />
          <button class="cart-send" @click="sendToCheckout(fudgeBrownie)">
            add to cart
          </button>
          <p class="item-blurb" v-if="fudgeBrownie.cart > 0">
            £{{ subTotal(fudgeBrownie) }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BrownieShop',
  props: {},
  data: function() {
    return {
      id: -1,
      classicBrownie: {
        name: 'classic brownies',
        cart: 0,
        price: 0,
        unitPrice: 12,
        id: 0
      },
      darkChocBrownie: {
        name: 'dark chocolate brownies',
        cart: 0,
        price: 0,
        unitPrice: 13,
        id: 0
      },
      caramelBrownie: {
        name: 'salted caramel brownies',
        cart: 0,
        price: 0,
        unitPrice: 12.5,
        id: 0
      },
      fudgeBrownie: {
        name: 'fudge brownies',
        cart: 0,
        price: 0,
        unitPrice: 12.5,
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
      this.id++
      product.id = this.id
      this.$emit('send-to-checkout', product)

      /*
      product.cart = 0
      product.id = 0
      */
    }
  }
}
</script>

<style scoped>
div.shop {
  clear: both;
  display: block;
  height: 470px;
  margin-left: 2rem;
  margin-right: 2rem;
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
