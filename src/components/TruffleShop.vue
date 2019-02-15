<template>
  <div>
    <div class="shop">
      <hr />
      <br />
      <div class="item-container">
        <div class="item-card">
          <img class="item-pic" src="../assets/truffles2.jpg" />
          <div class="item-text-container">
            <p class="item-blurb" style="font-size:1rem">
              <b>milk chocolate</b>
            </p>
            <br />
            <p class="item-blurb">smooth, rich milk chocolate truffles</p>
            <p class="item-blurb">that will melt in your mouth</p>
            <br />
            <p class="item-blurb" style="font-style:italic; text-align:center">
              £10.00 per box
            </p>
            <p class="item-blurb" style="font-style:italic; text-align:center">
              of 10 truffles
            </p>
            <button class="cart-add" @click="cartMinus(milkChocTruffle)">
              -
            </button>
            <span style="font-size:0.8rem">{{ milkChocTruffle.cart }}</span>
            <button class="cart-add" @click="cartAdd(milkChocTruffle)">
              +
            </button>
            <br />
            <button class="cart-send" @click="sendToCheckout(milkChocTruffle)">
              add to cart
            </button>
            <p v-if="milkChocTruffle.cart > 0">
              £{{ subTotal(milkChocTruffle) }}
            </p>
          </div>
        </div>
        <div class="item-card">
          <img class="item-pic" src="../assets/truffles2.jpg" />
          <div class="item-text-container">
            <p class="item-blurb" style="font-size:1rem">
              <b>dark chocolate</b>
            </p>
            <br />
            <p class="item-blurb">smooth, rich milk chocolate truffles</p>
            <p class="item-blurb">that will melt in your mouth</p>
            <br />
            <p class="item-blurb" style="font-style:italic; text-align:center">
              £10.00 per box
            </p>
            <p class="item-blurb" style="font-style:italic; text-align:center">
              of 10 truffles
            </p>
            <button class="cart-add" @click="cartMinus(darkChocTruffle)">
              -
            </button>
            <span style="font-size:0.8rem">{{ darkChocTruffle.cart }}</span>
            <button class="cart-add" @click="cartAdd(darkChocTruffle)">
              +
            </button>
            <br />
            <button class="cart-send" @click="sendToCheckout(darkChocTruffle)">
              add to cart
            </button>
            <p v-if="darkChocTruffle.cart > 0">
              £{{ subTotal(darkChocTruffle) }}
            </p>
          </div>
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
      if (product.cart > 0) {
        this.id += 1
        product.id = this.id
        this.$emit('send-to-checkout', product)
      }
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
  width: 50%;
  margin-left: auto;
  margin-right: auto;
  overflow-x: scroll;
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

@media screen and (max-width: 600px) {
  .item-container {
    width: 60%;
  }
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
}
</style>
