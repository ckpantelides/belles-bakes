<template>
  <div class="image product">
    <img :src="imgSrc" />
  </div>
</template>

<script>
export default {
  name: 'HeroImage',
  props: {
    imgSrc: String
  },
  data: function() {
    return {}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style></style>
