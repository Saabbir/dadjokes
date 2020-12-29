<template>
  <!-- Consult https://nuxtjs.org/docs/2.x/concepts/views#error-page for this page -->
  <div class="page-content">
    <div class="container text-center">
      <h1 v-if="error.statusCode === 404">Page not found</h1>
      <h1 v-else>An error occurred</h1>
      <div class="button-container">
        <NuxtLink to="/" class="button">Go back to home page</NuxtLink>
      </div>
    </div>
  </div>
</template>

<script>/* eslint-disable */
  export default {
    props: ['error'],
    head() {
      return {
        title: 'Error',
        meta: [
          {
            hid: 'description',
            name: 'description',
            content: 'Error Page'
          }
        ]
      }
    },
  }
</script>

<style scoped>
  h1 {
    font-size: 3rem;
  }
</style>