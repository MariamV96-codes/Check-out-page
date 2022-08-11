<template>
  <div class="cardContainer" :class="{ 'show-back': showBack}">
    <div class="front" >
      <div class="imgs">
        <img src="../assets/Images/chip.png" alt="chip" />
        <img src="../assets/Images/visa.png" alt="card logo" />
      </div>
      <div  class="cardnumber" > {{cardNumber}} **** **** **** **** </div>
      <div class="flex-container">
        <div class="output">
          <span>card holder </span>
          <div class="card-name" >{{cardName}}</div>
        </div>
        <div class="output">
          <span>expires</span>
          <div class="expiration">
            <span class="exp-month"> {{cardDate}}mm/yy</span>
          </div>
        </div>
      </div>
    </div>
    <div class="back">
          <div class="stripe"></div>
            <div class="box">
                <span>cvv</span>
                <div class="cvv-box"> {{cardCvv}}</div>
                <img src="../assets/Images/visa.png" alt="card logo" />
            </div>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return{
    }
  },
 props:{
  cardNumber: Number,
  cardName:Text,
  cardDate: Date,
 cardCvv: Number,
 showBack: Boolean,
 },

 };
</script>

<style  scoped>
/* this style is applied when input is clicked */
.show-back {
  transform: rotateY(180deg);
}


.cardContainer {
  margin: 0 55px;
  position: relative;
  height: 250px;
  width: 400px;
  margin-bottom: -100px;
  border-radius: 15px;
  color: #fff;
  transition: transform 1s;
  transform-style: preserve-3d;
  cursor: pointer;
}
.front,.back {
  position: absolute;
  height: 100%;
  width: 100%;
  top: 0;
  left: 0;
  background: url("https://images.unsplash.com/photo-1447703693928-9cd89c8d3ac5?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1171&q=80");
  backface-visibility: hidden;
  box-shadow: 0 15px 25px rgba(0, 0, 0, 0.2);
  padding: 20px;
  border-radius: 15px;
  transition: transform 1s;
  transform-style: preserve-3d;
  cursor: pointer;
}
.imgs {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-top: 10px;
}
.imgs img:first-child {
  width: 50px;
}
.imgs img:nth-child(2) {
  width: 88px;
}
.cardnumber {
  padding: 30px 0;
  font-size: 22px;
  color: #fff;
}
.flex-container {
  display: flex;
  justify-content: space-between;
}
.back{
    padding: 20px 0;
    text-align: right;
    transform: rotateY(180deg);
   transition: transform 1s;
}
.stripe{
    background: rgba(0, 0, 0, 0.546);
    width: 100%;
    margin: 10px 0;
    height: 50px; 
}
 .box{
    padding: 0 20px;
}
.box span{
    color:#fff;
    font-size: 15px;
}

 .cvv-box{
    height: 30px;
    padding: 10px;
    margin-top: 5px;
    color:#333;
    background: #fff;
    border-radius: 5px;
    width: 100%;
    z-index: 1;
}
.box img{
    margin-top: 30px;
    height: 30px;
}

@media screen and (max-width: 977px) {
  .cardContainer {
    height: 210px;
    width: 330px;
    margin: 0 auto;
  }
}
</style>