<template>
  <div>
    <nuxt-link :to="`/jokes/${joke.id}`">
      <div class="joke" >
        {{ joke.joke }}
      </div>
    </nuxt-link>
  </div>
</template>

<script>/* eslint-disable */
  export default {
    props: ['joke']
  }
</script>

<style scoped>

</style>