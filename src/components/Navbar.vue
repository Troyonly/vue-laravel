<template>
  <h1>Hello Navbar</h1>
  <nav class="navbar">
    <div class="navbar-brand">
      <router-link to="/dashboard" class="navbar-item">Home</router-link>
    </div>
    <div class="navbar-menu">
      <div class="navbar-end">
        <router-link to="/add-contact" class="navbar-item">Add Contact</router-link>
        <button @click="logout" class="navbar-item">Logout</button>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  methods: {
    logout() {
      this.$router.push('/'); // Redirect to the login page after logout
    }
  }
};
</script>

<style scoped>
/* Add your navbar styles here */
</style>
