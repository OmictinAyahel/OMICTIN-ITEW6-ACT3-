<template>
  <div class="app-container" >

    <ProductList @add-to-cart="addToCart"></ProductList>
    <ShoppingCart :cartItems="cartItems" @remove-from-cart="removeFromCart"></ShoppingCart>

    <button @click="handleLogout" class="logout-btn">logout</button>
  </div>
</template>
<script>
import ProductList from '@/components/ProductList.vue';
import ShoppingCart from '@/components/ShoppingCart.vue';

export default {
  components: {
    ProductList,
    ShoppingCart
  },
  data() {
    return {
      cartItems: []
    };
  },
  methods: {
    handleLogout() {
            localStorage.removeItem('token')
            this.$router.push('/login')
        },

    addToCart(product) {
      const existingItem = this.cartItems.find(item => item.id === product.id);
      if (existingItem) {
        existingItem.quantity++;
      } else {
        this.cartItems.push({ ...product, quantity: 1 });
      }
    },
    removeFromCart(item) {
      const index = this.cartItems.findIndex(cartItem => cartItem.id === item.id);
      if (index !== -1) {
        this.cartItems.splice(index, 1);
      }
    }
  }
};
</script>
<style scoped>
.app-container {
  display: flex;
  justify-content: space-around;
  align-items: flex-start;
  margin: 0;
  padding: 0;
  background-size: cover;
  background-position: center;
  height: 98vh;
}

.logout-btn {
  width: 8%;
  padding: 10px;
  margin-top: -15px; 
  background-color: #4F6F52;
  color: white;
 border: none;
}
</style>