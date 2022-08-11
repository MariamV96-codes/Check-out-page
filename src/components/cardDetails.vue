<template>
  <div class="formOuterContainer">
    <CreditCard 
    :cardNumber="cardNumber"
     :cardName="cardName"
     :cardDate="cardDate"
     :cardCvv="cardCvv"
     :showBack="showBack"
    />
 

    <div class="formContent">
      <form action="#">
        <div class="inputbox">
          <span> card number </span>
          <input v-model="cardNumber" type="tel" maxlength="16"   />
        </div>
        <div class="inputbox">
          <span> name on card</span>
          <input
           type="text"
           v-model="cardName" />
        </div>
        <div class="dates">
          <div class="inputbox">
            <span>expiration date</span>
            <input  v-model="cardDate"
            type="date" />
          </div>
          <div class="inputbox cvv">
            <span>cvv</span>
            <input
             v-model="cardCvv" 
             type="tel" 
             maxlength="4"
             @focus="showBack = true"
             @blur="showBack = false"/>
          </div>
        </div>

        <button class="checkoutBtn">Check out</button>
      </form>
    </div>
  </div>
</template>

<script>
import CreditCard from "./creditCard.vue";
export default {
  data() {
    return {
     cardName:'',
     cardNumber:'',
     cardDate: '',
     cardCvv: '',
    showBack: false,
    };
  },

  components: {
    CreditCard
},

};
</script>

<style scoped>
input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}
input[type="date"]::-webkit-inner-spin-button,
input[type="date"]::-webkit-calendar-picker-indicator {
  display: none;
  -webkit-appearance: none;
}
.formOuterContainer {
  padding-right: 33px;
  max-width: 99%;
}

.formContent {
  display: flex;
  flex-direction: column;
  padding: 28px 30px;
  background-color: #42434c;
  max-width: 500px;
  color: #fff;
  box-shadow: 0 30px 60px 0 rgba(90, 116, 148, 0.4);
  border-radius: 10px;
}
.formOuterContainer form {
  margin-top: 100px;
  padding: 10px 0;
}
.inputbox {
  margin: 10px 0;
}
.formContent span {
  display: block;
  padding: 6px 0;
  color: rgb(250, 248, 248);
}

.formContent input {
  width: 100%;
  padding: 10px;
  color: #fff;

  background: transparent;
  border: none;
  border-bottom: 1px solid #000000;
}
form input:focus {
  background: transparent;
  border: none;
  border-bottom: 1px solid #f5eeee;
  outline: none;
}
.dates {
  margin-top: 24px;
  display: flex;
  justify-content: space-between;
}
.checkoutBtn {
  background-color: #2d7aed;
  color: #fff;
  border-radius: 5px;

  padding: 16px;
  margin-top: 50px;
  cursor: pointer;
  border: none;
  width: 100%;
}


@media screen and (max-width: 977px) {
  .formOuterContainer {
    margin: 0 auto;
  }
  .formContent {
    margin-top: -100px;
  }
  .cvv {
    padding-left: 70px;
  }
}
</style>