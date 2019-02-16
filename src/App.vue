<template>
  <div id="app">
    <div class="header">
      <h1 style="cursor:pointer" @click="updateComponent(reload)">
        B e l l e 's &nbsp;b a k e s
      </h1>
      <div class="cart">
        <img
          @click="updateComponent(checkoutComponent)"
          src="./assets/basket.png"
          style="cursor:pointer"
        />
        <span
          v-if="checkout > 0"
          @click="updateComponent(checkoutComponent)"
          style="font-size:0.75rem; cursor:pointer"
          >{{ checkout }}</span
        >
      </div>
      <br />

      <ol class="menu-list">
        <li class="menu-item">
          <a @mouseover="updatePic(brownies)" @click="updateComponent(brownies)"
            >brownies</a
          >
          <span>&nbsp;|</span>
        </li>
        <li class="menu-item">
          <a @mouseover="updatePic(truffles)" @click="updateComponent(truffles)"
            >&nbsp;truffles</a
          >
          <span>&nbsp;|</span>
        </li>
        <li class="menu-item">
          <a
            @mouseover="updatePic(subscriptions)"
            @click="updateComponent(subscriptions)"
            >&nbsp;subscription</a
          >
          <span>&nbsp;|</span>
        </li>
        <li class="menu-item">
          <a @mouseover="updatePic(about)" @click="updateComponent(about)"
            >&nbsp;faqs</a
          >
        </li>
      </ol>
    </div>

    <div class="component-wrapper">
      <component
        :is="currentComponent"
        :imgSrc="pic"
        :baskets="baskets"
        @send-to-checkout="updateCheckout"
        @update-cart-number="updateCartNumber"
      ></component>
    </div>
  </div>
</template>

<script>
import HeroImage from './components/HeroImage.vue'
import BrownieShop from './components/BrownieShop.vue'
import CupcakeShop from './components/CupcakeShop.vue'
import TruffleShop from './components/TruffleShop.vue'
import AboutBelle from './components/AboutBelle.vue'
import Subscriptions from './components/Subscriptions.vue'
import CheckoutComponent from './components/CheckoutComponent.vue'

export default {
  name: 'app',
  components: {
    HeroImage,
    BrownieShop,
    CupcakeShop,
    TruffleShop,
    AboutBelle,
    Subscriptions,
    CheckoutComponent
  },
  props: {
    msg: String
  },
  data: function() {
    return {
      checkout: 0,
      baskets: [],
      pic: require('./assets/about.jpg'),
      currentComponent: HeroImage,
      brownies: {
        pic: require('./assets/brownies.jpg'),
        currentComponent: BrownieShop
      },
      cupcakes: {
        pic: require('./assets/cupcakes.jpg'),
        currentComponent: CupcakeShop
      },
      truffles: {
        pic: require('./assets/truffles2.jpg'),
        currentComponent: TruffleShop
      },
      about: {
        pic: require('./assets/about.jpg'),
        currentComponent: AboutBelle
      },
      subscriptions: {
        pic: require('./assets/subscription.jpg'),
        currentComponent: Subscriptions
      },
      reload: {
        currentComponent: HeroImage
      },
      checkoutComponent: {
        currentComponent: CheckoutComponent
      }
    }
  },
  methods: {
    updatePic(category) {
      this.pic = category.pic
    },
    updateComponent(category) {
      this.currentComponent = category.currentComponent
    },
    updateCheckout(product) {
      this.checkout += product.cart
      // use spread operator to avoid mutation of original object
      /*
      this.baskets.push(product) */
      this.baskets.push({ ...product })
    },
    // this receives the totalBoxes emitted payload from CheckoutComponent whenever an item
    // is deleted from the checkout, and updates the number next to the cart icon (top-right corner)
    updateCartNumber(totalBoxes) {
      this.checkout = totalBoxes
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Comfortaa');

@font-face {
  font-family: 'moderneSans';
  src: url('./assets/DaddyLonglegsNF.ttf');
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  height: 100vh;
  width: 100vw;
  font-family: 'Comfortaa', cursive;
  font-size: 1.125rem;
  line-height: 1.5;
  padding: 0;
  color: black;
  background: white;
  text-rendering: optimizeLegibility;
}

div.header {
  height: 16vh;
  margin-bottom: 5px;
}

div.component-wrapper {
  height: 83vh;
  width: 100%;
  clear: both;
}

img {
  width: 100vw;
  height: 83vh;
  object-fit: cover;
  margin: 0;
}

.cart {
  float: right;
  vertical-align: middle;
}

ul {
  padding: 0;
  margin: 0;
  list-style: none;
}

h1 {
  text-transform: uppercase;
  font-family: moderneSans;
  font-size: 4rem;
  text-align: center;
  margin-top: -70px;
  margin-bottom: -30px;
  color: #331d0b;
  user-select: none;
}

a {
  color: #724520;
  text-decoration: none;
  transition: all 0.2s ease;
  font-weight: bold;
  font-size: 1rem;
}

.menu-list {
  clear: both;
  text-align: center;
  padding: 0;
  list-style: none;
  margin-top: -15px;
}

.menu-item {
  display: inline;
  user-select: none;
}

.menu-item :hover {
  color: #80522d79;
}

.cart {
  margin-top: -20px;
  margin-right: 3rem;
}
.cart img {
  height: 20px;
  width: auto;
}

@media screen and (max-width: 600px) {
  h1 {
    font-size: 3rem;
    margin-top: -65px;
  }

  div.header {
    height: 13vh;
  }
}
</style>
