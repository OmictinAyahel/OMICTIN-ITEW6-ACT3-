<template>
  <div>
    <nav class="main-nav">
      <router-link to="/login" class="nav-link">Login</router-link> |
      <router-link to="/shopping" class="nav-link">Shopping</router-link>
    </nav>
    <router-view/>
  </div>
</template>
<script>
export default {
  name: 'App',
  mounted() {
    if (!localStorage.getItem('token')) {
      this.$router.push('/login');
    }
  }
}
</script> 
<style scoped>
.main-nav {
  text-align: center;
  padding: 20px 0;
  background-color: #ffffff; 
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1); 
  margin-bottom: 20px;
}

.nav-link, .disabled {
  font-weight: 500; 
  color: #5F7161; 
  padding: 8px 15px;
  margin: 0 10px;
  text-decoration: none;
  transition: color 0.3s ease, background-color 0.3s ease;
  border-radius: 20px;
  display: inline-block; 
}

.nav-link:hover:not(.disabled) {
  color: #ffffff; 
  background-color: #6D8B74; 
}

.disabled {
  opacity: 0.5; 
  cursor: not-allowed;
}

.router-view {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
