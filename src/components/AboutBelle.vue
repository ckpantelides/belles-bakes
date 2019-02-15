<template>
  <div>
    <div class="shop">
      <hr />
      <br />

      <div class="faqs-container">
        <p class="question">How long will the brownies keep for?</p>

        <p>
          Our brownies will keep at their best for around 5 days when stored at
          room temperature in an airtight container. You can also freeze your
          brownies for up to a month – just make sure you’ve wrapped them.
        </p>

        <p class="question">Do you have gluten free or vegan brownies?</p>

        <p>
          All of our brownies contain gluten and dairy products. We are
          currently working hard to perfect a gluten free & vegan brownie. We
          also send tasters of our new flavours with orders at random each
          month!
        </p>

        <p class="question">How do my brownies arrive?</p>

        <p>
          Your brownies will arrive wrapped and enclosed in a postal box, along
          with a handwritten gift message of your choice, if you’ve added one.
          Your box will arrive via Royal Mail and will need to be signed for as
          it’s a little too big to fit through a letterbox. This way we can also
          let you track your order, and you will be emailed with your tracking
          number once your treats have been dispatched.
        </p>

        <p class="question">My brownies haven’t arrived, what do I do?</p>

        <p>
          If you’ve checked the Royal Mail website with your tracking number and
          you’re still having trouble, please contact us at
          hello@bellesbrownies.com, and we’ll get back to you as soon as we can.
          You can find out more information about the delivery options available
          to you here.
        </p>
        <p class="question">How to contact us?</p>
        <p>
          If you need to get in touch for any reason email us at
          hello@bellesbakes.com
        </p>
      </div>
    </div>
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
.faqs-container {
  width: 75%;
  margin-right: auto;
  margin-left: auto;
  background: white;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.8);
  height: 480px;
  padding: 2px 10px;
}

h2 {
  font-family: 'Comfortaa', cursive;
  font-size: 2rem;
  font-weight: 200;
  color: #58381e;
  margin-top: 25px;
}

p {
  color: #331d0b;
  font-size: 0.8rem;
}

p.question {
  font-weight: bold;
}

@media screen and (max-width: 600px) {
  .header {
    height: 13vh;
  }
  div.shop {
    background: white;
    overflow-y: scroll;
    margin-top: -15px;
  }

  hr {
    display: block;
    margin-top: 0;
  }

  .faqs-container {
    width: 90%;
    margin-left: auto;
    margin-right: auto;
    height: auto;
    box-shadow: none;
  }
}
</style>
