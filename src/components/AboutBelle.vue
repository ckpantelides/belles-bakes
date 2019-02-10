<template>
  <div>
    <hr />
    <div class="shop">
      <br />
      <h2>FAQs</h2>

      <p class="question">How long will the brownies keep for?</p>
      <br />
      <p>
        Our brownies will keep at their best for around 5 days when stored at
        room temperature in an airtight container. You can also freeze your
        brownies for up to a month – just make sure you’ve wrapped them.
      </p>
      <br />
      <p class="question">Do you have gluten free or vegan brownies?</p>
      <br />
      <p>
        All of our brownies contain gluten and dairy products. We are currently
        working hard to perfect a gluten free & vegan brownie. We also send
        tasters of our new flavours with orders at random each month!
      </p>
      <br />
      <p class="question">How do my brownies arrive?</p>
      <br />
      <p>
        Your brownies will arrive wrapped and enclosed in a postal box, along
        with a handwritten gift message of your choice, if you’ve added one.
        Your box will arrive via Royal Mail and will need to be signed for as
        it’s a little too big to fit through a letterbox. This way we can also
        let you track your order, and you will be emailed with your tracking
        number once your treats have been dispatched.
      </p>
      <br />
      <p class="question">My brownies haven’t arrived, what do I do?</p>
      <br />
      <p>
        If you’ve checked the Royal Mail website with your tracking number and
        you’re still having trouble, please contact us at
        hello@bellesbrownies.com, and we’ll get back to you as soon as we can.
        You can find out more information about the delivery options available
        to you here.
      </p>
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
  height: 470px;
  margin-left: 8rem;
  margin-right: 8rem;
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
  color: #331d0b;
  font-size: 0.8rem;
}

p.question {
  font-weight: bold;
}
</style>
