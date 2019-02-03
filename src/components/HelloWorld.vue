<template>
  <div class="hello">
    <h1>Belle's bakes</h1>
    <hr />
    <br />
    <div class="nav-left">
      <ol class="menu-list">
        <li class="menu-item">
          <a
            href="#"
            @mouseover="updatePic(brownies)"
            @click="updateComponent(brownies)"
            >Brownies</a
          >
        </li>
        <li class="menu-item">
          <a
            href="#"
            @mouseover="updatePic(cupcakes)"
            @click="updateComponent(cupcakes)"
            >Cupcakes</a
          >
        </li>
        <li class="menu-item">
          <a
            href="#"
            @mouseover="updatePic(truffles)"
            @click="updateComponent(truffles)"
            >Truffles</a
          >
        </li>
        <li class="menu-item">
          <a
            href="#"
            @mouseover="updatePic(about)"
            @click="updateComponent(about)"
            >About</a
          >
        </li>
        <li class="menu-item">
          <img
            class="cupcake"
            @click="updateComponent(reload)"
            src="../assets/cupcake.png"
          />
        </li>
      </ol>
    </div>

    <div class="image product">
      <component :is="currentComponent" :imgSrc="pic"></component>
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

export default {
  components: {
    HeroImage
  },
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data: function() {
    return {
      pic: require('../assets/brownies.jpg'),
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
      reload: {
        currentComponent: HeroImage
      }
    }
  },
  methods: {
    updatePic(category) {
      this.pic = category.pic
    },
    updateComponent(category) {
      this.currentComponent = category.currentComponent
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

* {
  box-sizing: border-box;
}

body {
  /*
  font-family: 'Josefin Sans', sans-serif;
  */
  font-family: 'Comfortaa', cursive;
  font-size: 1.125rem;
  line-height: 1.5;
  margin: 0;
  padding: 0;
  color: black;
  background: white;
  text-rendering: optimizeLegibility;
}

ul {
  padding: 0;
  margin: 0;
  list-style: none;
}

h1 {
  text-transform: uppercase;
  font-family: 'Limelight', cursive;
  font-size: 3.7rem;
  text-align: left;
  margin-left: 180px;
  margin-top: -50px;
  margin-bottom: -10px;
  color: #58381e;
  /* #80532d; */
  /* #8c6833; */
}

.cupcake {
  height: 20px;
  width: auto;
  margin-left: 20px;
  margin-top: 10px;
}

a {
  color: #58381e;
  text-decoration: none;
  transition: all 0.2s ease;
  font-weight: bold;
}

img {
  width: 500px;
  height: auto;
  object-fit: cover;
}

hr {
  display: block;
  margin-top: 0.5em;
  margin-bottom: 0.5em;
  margin-left: 180px;
  margin-right: 290px;
  border-style: solid;
  border-width: 1.5px;
  color: #80532d;
}

.head {
  display: block;
  width: 100%;
  text-align: left;
  padding-top: 0px;
}

.nav-left {
  float: left;
  display: block;
  width: 15%;
}

.menu-list {
  text-align: left;
  margin-left: 180px;
  padding: 0;
  list-style: none;
}

.menu-item :hover {
  color: #80522d79;
}
</style>
