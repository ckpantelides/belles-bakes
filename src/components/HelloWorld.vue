<template>
  <div class="hello">
    <h1 style="cursor:pointer" @click="updateComponent(reload)">
      B e l l e 's &nbsp;b a k e s
    </h1>
    <div class="cart">
      <img
        @click="updateComponent(checkoutComponent)"
        src="../assets/basket.png"
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
    <div class="nav-left">
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
          <a @mouseover="updatePic(about)" @click="updateComponent(about)"
            >&nbsp;about</a
          >
          <span>&nbsp;|</span>
        </li>
        <li class="menu-item">
          <a
            @mouseover="updatePic(about)"
            @click="updateComponent(subscriptions)"
            >&nbsp;subscription</a
          >
          <!--
          <span>&nbsp;|</span>
          -->
        </li>
        <!--
        <img
          class="cupcake"
          @click="updateComponent(reload)"
          src="../assets/cupcake.png"
        />
        -->
      </ol>
    </div>

    <div class="image product">
      <component
        :is="currentComponent"
        :imgSrc="pic"
        :baskets="baskets"
        @send-to-checkout="updateCheckout"
        @update-cart-number="updateCartNumber"
      ></component>
      <!--
      <HeroImage :imgSrc="pic" />
      -->
    </div>
  </div>
</template>

<script>
import HeroImage from '../components/HeroImage.vue'
import BrownieShop from '../components/BrownieShop.vue'
import CupcakeShop from '../components/CupcakeShop.vue'
import TruffleShop from '../components/TruffleShop.vue'
import AboutBelle from '../components/AboutBelle.vue'
import Subscriptions from '../components/Subscriptions.vue'
import CheckoutComponent from '../components/CheckoutComponent.vue'

export default {
  components: {
    HeroImage,
    BrownieShop,
    CupcakeShop,
    TruffleShop,
    AboutBelle,
    Subscriptions,
    CheckoutComponent
  },
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data: function() {
    return {
      checkout: 0,
      baskets: [],
      pic: require('../assets/about.jpg'),
      currentComponent: HeroImage,
      brownies: {
        pic: require('../assets/brownies.jpg'),
        currentComponent: BrownieShop
      },
      cupcakes: {
        pic: require('../assets/cupcakes.jpg'),
        currentComponent: CupcakeShop
      },
      truffles: {
        pic: require('../assets/truffles.jpg'),
        currentComponent: TruffleShop
      },
      about: {
        pic: require('../assets/about.jpg'),
        currentComponent: AboutBelle
      },
      subscriptions: {
        pic: require('../assets/about.jpg'),
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
@import url('https://fonts.googleapis.com/css?family=Josefin+Sans');
@import url('https://fonts.googleapis.com/css?family=Comfortaa');
@import url('https://fonts.googleapis.com/css?family=Alfa+Slab+One');
@import url('https://fonts.googleapis.com/css?family=Alegreya+Sans+SC');
@import url('https://fonts.googleapis.com/css?family=Kodchasan');
@import url('https://fonts.googleapis.com/css?family=Limelight');

@font-face {
  font-family: 'moderneSans';
  src: url('../assets/DaddyLonglegsNF.ttf');
}

* {
  box-sizing: border-box;
}

body {
  font-family: 'Comfortaa', cursive;
  font-size: 1.125rem;
  line-height: 1.5;
  margin: 0;
  padding: 0;
  color: black;
  background: white;
  text-rendering: optimizeLegibility;
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
  /*
  font-family: 'Limelight', cursive;
  */
  font-family: moderneSans;
  font-size: 4rem;
  /*
  font-size: 5rem;
  text-align: left;
  margin-left: 30px;
  */
  text-align: center;
  margin-top: -70px;
  margin-bottom: -30px;
  color: #331d0b;
  /* #80532d; */
  /* #8c6833; */
}

.cupcake {
  height: 20px;
  width: auto;
  margin-left: 10px;
  /*
  display: inline;
  */
  vertical-align: middle;
  border: none;
}

a {
  color: #724520;
  text-decoration: none;
  transition: all 0.2s ease;
  font-weight: bold;
  font-size: 1rem;
}

img {
  /*
  width: 1220px; 
  margin-left: -10px;
  height: 500px;
  */
  width: 100%;
  height: 535px;
  object-fit: cover;

  margin-top: -10px;
  /*
  border: solid 1px #58381e;
  */
}
/*
hr {
  display: block;
  margin-top: 0.5em;
  margin-bottom: -25px;
  margin-left: 30px;
  margin-right: 40px;
  border-style: solid;
  border-width: 1.5px;
  color: #331d0b;
}
*/
.head {
  display: block;
  width: 100%;
  text-align: left;
  padding-top: 0px;
}

.nav-left {
  /*
  float: left;
  */
  display: block;
  /* width: 15%; */
}

.image product {
  width: 100%;
  clear: both;
}

.menu-list {
  /*
  text-align: left;
  margin-left: 30px;
  */
  clear: both;
  text-align: center;
  padding: 0;
  list-style: none;
  /*
  margin-top: 5px;
  */
  margin-top: -15px;
}

.menu-item {
  display: inline;
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
</style>
