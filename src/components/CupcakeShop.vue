<template>
  <div class="shop">
    <h2>Cupcake shop</h2>
    <p>Chocolate</p>
    <p>Vanilla</p>
  </div>
</template>

<script>
export default {
  name: 'CupcakeShop',
  props: {},
  data: function() {
    return {}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div.shop {
  clear: both;
  display: block;
  height: 470px;
  border: solid 1px #58381e;
  padding: 15px;
  margin: 20px;
}

h2 {
  text-transform: uppercase;
  font-family: 'Limelight', cursive;
  font-size: 3rem;
  color: #58381e;
  margin-top: -20px;
}

p {
  margin-top: -20px;
}
</style>
