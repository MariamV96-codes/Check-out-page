<template>
  <div class="cartContainer">
    <h2>Shopping Cart</h2>
    <div
      class="content"
      v-for="(product, index) in products"
      :key="product.name"
    >
      <img :src="product.image" alt="product img" />
      <div class="textContainer">
        <p>{{ product.name }}</p>
        <span> {{ product.id }}</span>
      </div>

      <div class="wrapper">
        <a @click="decrementNum(index)" href="#" class="btn quantity">-</a>
        <span class="num">{{ product.quantity }}</span>
        <a @click="incrementNum(index)" href="#" class="btn quantity">+</a>
      </div>
      <p>${{ itemtotal(index) }}</p>
      <a @click="removeElement(index)" href="#" class="btn remove">X</a>
    </div>
    <div class="price">
      <a href="#" class="btn-arrow">continue shopping</a>
      <p>
        subtotal:<span> ${{ totalCart }} </span>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      products: [
        {
          image: require("@/assets/Images/momo.png"),
          name: "Chicken momo",
          id: "#4297654",
          quantity: 1,
          price: 10,
        },
        {
          image: require("@/assets/Images/huevos-con-patatas_1-removebg-preview.png"),
          name: "huevos patatas",
          id: "#9365539",
          quantity: 1,
          price: 8,
        },
        {
          image: require("@/assets/Images/pasta-removebg-preview.png"),
          name: "Carbonar Pasta",
          id: "#2947205",
          quantity: 1,
          price: 5,
        },
      ],
    };
  },
  methods: {
    incrementNum(index) {
      const num = this.products[index]
      num.quantity++;
    },
    decrementNum(index) {
      if (this.products[index].quantity !== 0) this.products[index].quantity--;
    },
    itemtotal(index) {
      return this.products[index].quantity * this.products[index].price;
    },
    removeElement(index) {
      this.products.splice(index, 1);
    },
  },

  computed: {
    totalCart() {
      let total = 0;
      for (let index = 0; index < this.products.length; index++) {
        const element = this.products[index];
        total = total + element.quantity * element.price;
      }
      return total;
    },
  },
};



</script>

<style scoped>
a {
  text-decoration: none;
}
.cartContainer {
  margin-right: 5%;
  width: 100%;
}
.cartContainer h2 {
  margin-bottom: 16px;
}
.content {
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  border-bottom: 1px #e9ebec solid;
  padding-bottom: 8px;
}

.content p {
  font-size: 1.4rem;
  font-weight: 600;
}
.textContainer * {
  padding: 1.2px 0;
}

.textContainer span {
  color: #bcbcbf;
}
.content img {
  width: 16%;
}

.content span {
  display: block;
}

.num {
  padding: 4px;
  width: 41px;
  text-align: center;
  border: 1px rgb(192, 192, 192) solid;
  border-radius: 3px;
  font-size: 1rem;
  color: #b1b1b1;
  font-weight: 600;
}
.wrapper {
  display: flex;
  justify-content: center;
  align-content: center;
}
.btn {
  background-color: transparent;
  border: none;
  cursor: pointer;
  font-size: 1.7rem;
  font-weight: 500;
  color: #000;
}
.quantity {
  margin: 0 19px;
  align-self: flex-end;
  text-align: center;
}

.price {
  display: flex;
  justify-content: space-between;
  padding: 22px;
  font-size: 1.2rem;
  color: #000;
  font-weight: 600;
}

.price p {
  color: #939396;
  font-weight: 600;
}
.price span {
  font-size: 1.4rem;
  color: #000;
}

@media screen and (max-width: 1721px) and (min-width: 481px) {
  .content {
    padding: 16px;
    height: 28%;
  }
  .content * {
    margin: 10px 11px;
  }
}
</style>