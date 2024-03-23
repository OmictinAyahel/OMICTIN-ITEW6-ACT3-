<template>
  <div class="login-container">
    <h2>Login</h2>
    <form @submit.prevent="handleLogin" class="login-form">
      <div class="form-group">
        <label for="email">Email:</label>
        <input id="email" v-model="email" type="email" required>
      </div>
      <div class="form-group">
        <label for="password">Password:</label>
        <input id="password" v-model="password" type="password" required>
      </div>
      <button type="submit">SUBMIT</button>
    </form>
  </div>
</template>
<script>
export default {
  data() {
    return {
      email: '',
      password: '',
    };
  },
  methods: {
    handleLogin() {
      // Default credentials
      const defaultEmail = 'student@gmail.com';
      const defaultPassword = 'student123';

      if (this.email === defaultEmail && this.password === defaultPassword) {
        localStorage.setItem('token', '12345');
        this.$router.push({ name: 'shopping' });
      } else {
        alert('Invalid email or password. Please try again.');
      }
    }
  }
}
</script>
<style scoped>
h2 {
  text-align: center;
  color: #3C4F76; 
  margin-bottom: 30px;
}

.login-container {
  max-width: 400px;
  margin: 5% auto; 
  padding: 40px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); 
  border-radius: 8px; 
  border: 1px solid #3C4F76;

}

.form-group {
  margin-bottom: 20px; 
}

label {
  display: block;
  color: #3C4F76; 
  margin-bottom: 5px; 
}

input[type="email"], input[type="password"] {
  width: calc(100% - 20px);
  padding: 12px 10px;
  margin: 10px 0;
  border-radius: 5px;
  border: 2px solid #3C4F76; 
  background-color: #ffffff; 
}

button {
  display: block;
  width: 60%;
  padding: 12px;
  background-color: #7F9F80; 
  color: white;
  cursor: pointer;
  margin: 20px auto; 
  transition: background-color 0.3s ease; 
  border: none;
}

button:hover {
  background-color: #2C3E50;
}
</style>
