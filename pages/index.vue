<template>
  <div class="page-content">
    <div class="container">
      <div>
        <img src="~/assets/images/funny-dad.png" alt="Funny Dad">
      </div>
      <div class="button-container text-center">
        <nuxt-link to="/jokes" class="button">Checkout More Jokes Like This</nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>/* eslint-disable */
export default {
  head() {
    return {
      title: 'Welcome to Dad Jokes',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Best place for corny dad jokes'
        }
      ]
    }
  }  
}
</script>
