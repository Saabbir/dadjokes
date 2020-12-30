<template>
  <div class="navbar">
    <div class="navbar__container container">
      <div class="navbar__logo-container">
        <nuxt-link to="/">
          <div class="navbar__logo">Dad Jokes</div>
        </nuxt-link>
      </div>
      <nav class="navbar__nav">
        <nuxt-link to="/" exact>Home</nuxt-link>
        <nuxt-link to="/jokes">Jokes</nuxt-link>
      </nav>
    </div>
  </div>
</template>

<script>/* eslint-disable */
  export default {
    name: 'Navbar'
  }
</script>

<style scoped>

.navbar {
  padding: 1rem 0;
  background-color: #fafafa;
  border-bottom: 1px solid #ddd;
}

.navbar__logo-container a {
  text-decoration: none;
}

.navbar__container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.navbar__logo {
  background-color: #000;
  color: white;
  padding: 10px 15px;
  display: block;
  text-transform: uppercase;
  font-weight: bold;
}

.navbar__nav a {
  display: inline-block;
}

.navbar__nav a.nuxt-link-active {
  font-weight: bold;
}

.navbar__nav a:not(:last-child) {
  margin-right: 1rem;
}
</style>