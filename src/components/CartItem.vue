<template>
  <div class="cart-item">
    <span>{{ item.name }} - Php {{ item.price }} x {{ item.quantity }}</span>
    <button @click="removeFromCart" class="btn remove">Remove</button>
  </div>
</template>

<script>
export default {
  props: ['item'],
  methods: {
    removeFromCart() {
      this.$emit('remove-from-cart', this.item);
    }
  }
};
</script>

<style>
.cart-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  border-bottom: 1px solid #eee;
}

.btn {
  background-color: #007bff;
  color: #fff;
  border: none;
  padding: 5px 10px;
  font-size: 14px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.btn.remove:hover {
  background-color: #0056b3;
}
</style>
