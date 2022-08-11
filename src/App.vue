<template>
  <main>
    <nav>
      <h1>Kyoto</h1>
      <ul>
        <li>search</li>
        <li>about</li>
        <li>log in</li>
      </ul>
    </nav>
    <div class="mainContainer">
      <cart />

      <card-form />
    </div>
  </main>
</template>

<script>
import cart from "./components/shoppingCart.vue";
import cardForm from "./components/cardDetails.vue";

export default {
  name: "App",
  components: {
    cart,
    cardForm,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Raleway:wght@400;600&display=swap");

html {
  font-size: 14px;
}
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
  font-family: "Raleway", sans-serif;
  text-transform: capitalize;
}

nav {
  display: flex;
  min-height: 8vh;
  justify-content: space-between;
  padding-top: 1rem;
  border-bottom: 1px rgba(128, 128, 128, 0.397) solid;
  text-align: center;
}
nav h1 {
  padding: 0rem 1.3rem;
  letter-spacing: 0.2rem;
}
ul {
  display: flex;
}
li {
  list-style: none;
  padding: 0.4em 1.6rem;
  cursor: pointer;
  font-size: 1.2rem;
  letter-spacing: 0.1rem;
}
.mainContainer {
  /* display: flex;
  justify-content: space-around; */

  display: flex;
  /* padding: 50px 22px; */
  margin: 23px 33px;
}
@media screen and (max-width: 977px) {
  .mainContainer {
    flex-direction: column;
  }
}
</style>
