<template>
  <div>
    <ul class="list">
      <li v-for="product in products" :key="product.id" class="item">
        <div class="info">
          <img :src="product.image" alt="Product Image" class="image">
          <div>
            <p class="name">{{ product.name }}</p>
            <p class="price">Php {{ product.price }}</p>
          </div>
        </div>
        <button @click="addToCart(product)" class="btn add">Add to Cart</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      products: [
      { id: 1, name: 'Espresso', price: 180, image: '/img/img1.jpg' },
          { id: 2, name: 'Cappuccino', price: 130, image: '/img/img2.jpg' },
          { id: 3, name: 'Latte', price: 150, image: '/img/img3.jpg' },
          { id: 4, name: 'Americano', price: 100, image: '/img/img4.jpg' },
          { id: 5, name: 'Mocha', price: 145, image: '/img/img5.jpg' },
          { id: 6, name: 'Macchiato', price: 120, image: '/img/img6.jpg' },
          { id: 7, name: 'Flat White', price: 160, image: '/img/img7.jpg' },
          { id: 8, name: 'Affogato', price: 190, image: '/img/img8.jpg' },
          { id: 9, name: 'Irish Coffee', price: 170, image: '/img/img9.jpg' }
      ]
    };
  },
  methods: {
    addToCart(product) {
      this.$emit('add-to-cart', product);
    }
  }
};
</script>

<style>
.title {
  font-size: 24px;
  color: #333;
  margin-bottom: 20px;
}

.list {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* Adjusted for 3 items per row */
  gap: 20px;
  background-color:  #4F6F52;
  padding: 50px;
  margin-top: -1px;
  border-radius: 10px;
  
}

.item {
  background-color: white;
  padding: 20px;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  display: flex;
  flex-direction: column;
}

.info {
  display: flex;
  align-items: center;
}

.image {
  width: 80px;
  height: 80px;
  border-radius: 15px;
  margin-right: 20px;
}

.name, .price {
  margin: 0;
}

.btn {
  margin-top: auto;
  padding: 8px 15px;
  background-color: #5F8670;
  color: white;
  border: none;
  cursor: pointer;
  transition: background-color 0.3s;
  margin-top: 5px;
}

.btn.add:hover {
  background-color: #0056b3;
}
</style>
