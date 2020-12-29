<template>
  <div class="page-content">
    <div class="container">
      <h1>Dad jokes</h1>
      <ul class="jokes-list">
        <Joke v-for="joke in jokes" :key="joke.id" :joke="joke" />
      </ul>
    </div>
  </div>
</template>

<script>/* eslint-disable */
  import Joke from '~/components/Joke.vue';
  export default {
    head() {
      return {
        title: 'Dad Jokes',
        meta: [
          {
            hid: 'description',
            name: 'description',
            content: 'Best place for corny dad jokes'
          }
        ]
      }
    },    
    components: {
      Joke
    },
    async asyncData({ $axios }) {
      const config = {
        headers: {
          Accept: 'application/json'
        }
      }

      try {
        const response = await $axios.get('https://icanhazdadjoke.com/search', config)
      
        return {
          jokes: response.data.results
        }        
      } catch (error) {
        console.log(error.message)

        return {
          jokes: []
        }
      }
    },
  }
</script>

<style scoped>
  .jokes-list {
    margin: 0;
    padding: 0;
    list-style: none;
  }
</style>