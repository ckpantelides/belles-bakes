<template>
  <div>
    <div class="shop">
      <hr />
      <br />
      <div class="item-container">
        <div class="item-card">
          <img class="item-pic" src="../assets/brownies.jpg" />
          <div class="item-text-container">
            <p class="item-blurb" style="font-size:1rem">
              <b>classic</b>
            </p>
            <br />
            <p class="item-blurb">smooth, rich milk chocolate brownies</p>
            <p class="item-blurb">that will melt in your mouth</p>
            <br />
            <p class="item-blurb" style="font-style:italic; text-align:center">
              £12.00 per box
            </p>
            <p class="item-blurb" style="font-style:italic; text-align:center">
              of 8 brownies
            </p>
            <button class="cart-add" @click="cartMinus(classicBrownie)">
              -
            </button>
            <span class="cart-total">{{ classicBrownie.cart }}</span>
            <button class="cart-add" @click="cartAdd(classicBrownie)">+</button>
            <br />
            <button class="cart-send" @click="sendToCheckout(classicBrownie)">
              add to cart
            </button>
            <p v-if="classicBrownie.cart > 0" class="cart-total">
              £{{ subTotal(classicBrownie) }}
            </p>
          </div>
        </div>
        <div class="item-card">
          <img class="item-pic" src="../assets/brownies.jpg" />
          <div class="item-text-container">
            <p class="item-blurb" style="font-size:1rem">
              <b>dark chocolate & sea salt</b>
            </p>
            <br />
            <p class="item-blurb">smooth, rich brownies</p>
            <p class="item-blurb">that will melt in your mouth</p>
            <br />
            <p class="item-blurb" style="font-style:italic; text-align:center">
              £13.00 per box
            </p>
            <p
              p
              class="item-blurb"
              style="font-style:italic; text-align:center"
            >
              of 8 brownies
            </p>
            <button class="cart-add" @click="cartMinus(darkChocBrownie)">
              -
            </button>
            <span class="cart-total">{{ darkChocBrownie.cart }}</span>
            <button class="cart-add" @click="cartAdd(darkChocBrownie)">
              +
            </button>
            <br />
            <button class="cart-send" @click="sendToCheckout(darkChocBrownie)">
              add to cart
            </button>
            <p v-if="darkChocBrownie.cart > 0" class="cart-total">
              £{{ subTotal(darkChocBrownie) }}
            </p>
          </div>
        </div>
        <div class="item-card">
          <img class="item-pic" src="../assets/brownies.jpg" />
          <div class="item-text-container">
            <p class="item-blurb" style="font-size:1rem">
              <b>salted caramel</b>
            </p>
            <br />
            <p class="item-blurb">smooth, rich brownies</p>
            <p class="item-blurb">that will melt in your mouth</p>
            <br />
            <p class="item-blurb" style="font-style:italic; text-align:center">
              £12.50 per box
            </p>
            <p
              p
              class="item-blurb"
              style="font-style:italic; text-align:center"
            >
              of 8 brownies
            </p>
            <button class="cart-add" @click="cartMinus(caramelBrownie)">
              -
            </button>
            <span class="cart-total">{{ caramelBrownie.cart }}</span>
            <button class="cart-add" @click="cartAdd(caramelBrownie)">+</button>
            <br />
            <button class="cart-send" @click="sendToCheckout(caramelBrownie)">
              add to cart
            </button>
            <p v-if="caramelBrownie.cart > 0" class="cart-total">
              £{{ subTotal(caramelBrownie) }}
            </p>
          </div>
        </div>
        <div class="item-card">
          <img class="item-pic" src="../assets/brownies.jpg" />
          <div class="item-text-container">
            <p class="item-blurb" style="font-size:1rem">
              <b>fudge</b>
            </p>
            <br />
            <p class="item-blurb">smooth, rich brownies</p>
            <p class="item-blurb">that will melt in your mouth</p>
            <br />
            <p class="item-blurb" style="font-style:italic; text-align:center">
              £12.50 per box
            </p>
            <p
              p
              class="item-blurb"
              style="font-style:italic; text-align:center"
            >
              of 8 brownies
            </p>
            <button class="cart-add" @click="cartMinus(fudgeBrownie)">-</button>
            <span class="cart-total">{{ fudgeBrownie.cart }}</span>
            <button class="cart-add" @click="cartAdd(fudgeBrownie)">+</button>
            <br />
            <button class="cart-send" @click="sendToCheckout(fudgeBrownie)">
              add to cart
            </button>
            <p v-if="fudgeBrownie.cart > 0" class="cart-total">
              £{{ subTotal(fudgeBrownie) }}
            </p>
          </div>
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
      id: 0,
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
      if (product.cart > 0) {
        this.id++
        product.id = this.id
        this.$emit('send-to-checkout', product)
      }
    }
  }
}
</script>

<style scoped>
.header {
  height: 13vh;
}

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

h2 {
  font-family: 'Comfortaa', cursive;
  font-size: 2rem;
  font-weight: 200;
  color: #58381e;
  margin-top: 25px;
}

p {
  margin-top: 0px;
  font-size: 0.75rem;
}

p.item-blurb {
  font-size: 0.75rem;
  margin: 0rem;
  text-align: left;
}

.item-container {
  display: flex;
  width: 90%;
  margin-left: auto;
  margin-right: auto;
  margin-top: -5px;
  overflow-x: auto;
}

.item-card {
  flex: 1;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.4);
  transition: 0.3s;
  margin: 1%;
  min-width: 250px;
  min-height: 440px;
  background: white;
}

.item-pic {
  height: 200px;
  width: 100%;
}

.item-text-container {
  padding: 2px 16px;
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

.cart-total {
  font-size: 0.8rem;
}

@media screen and (max-width: 600px) {
  div.shop {
    background: white;
  }

  hr {
    display: block;
  }

  .item-container {
    display: flex;
    width: 90%;
    margin-left: auto;
    margin-right: auto;
    flex-wrap: nowrap;
    overflow-x: auto;
  }

  .item-card {
    flex: 0 0 auto;
    max-width: 90%;
    box-shadow: none;
  }

  span.cart-total {
    font-size: 1rem;
    padding: 0 5px 0 5px;
  }

  button.cart-send,
  button.cart-add {
    font-size: 0.9rem;
  }
}
</style>
