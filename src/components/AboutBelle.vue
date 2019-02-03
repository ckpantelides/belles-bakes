<template>
  <div class="shop">
    <h2>About Belle</h2>
    <p>Belle's an old koala bum beanbag</p>
    <p>Kyri makes much better truffles</p>
  </div>
</template>

<script>
export default {
  name: 'AboutBelle',
  props: {},
  data: function() {
    return {}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.shop {
  text-align: centre;
  margin: 10px;
}

h2 {
  text-transform: uppercase;
  font-family: 'Limelight', cursive;
  font-size: 3rem;
  margin-left: 180px;
  margin-top: -50px;
  margin-bottom: -10px;
  color: #58381e;
}
</style>
