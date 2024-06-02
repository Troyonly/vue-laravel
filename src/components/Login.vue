<template>
  <div class="login-container">
    <h1>Login</h1>
    <form @submit.prevent="handleSubmit">
      <div class="form-group">
        <label for="username">Username</label>
        <input
          type="text"
          id="username"
          v-model="username"
          required
        />
      </div>
      <div class="form-group">
        <label for="password">Password</label>
        <input
          type="password"
          id="password"
          v-model="password"
          required
        />
      </div>
      <button type="submit">Login</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: '',
      password: '',
    };
  },
  methods: {
    handleSubmit() {
      // Replace with your login logic
      if (this.username === 'admin' && this.password === 'password') {
        alert('Login successful!');
        // Navigate to the dashboard after successful login
        this.$router.push('/dashboard');
      } else {
        alert('Invalid username or password');
      }
    },
  },
};
</script>

<style scoped>
/* Add your styles here */
</style>
