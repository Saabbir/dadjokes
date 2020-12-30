<template>
  <div class="page-content">
    <div class="container">
      <div class="back-to-jokes">
        <nuxt-link to="/jokes">&laquo; Back to Jokes</nuxt-link>
      </div>
      <div class="joke--single">
        <p v-if="!randomJoke">{{ joke.joke }}</p>
        <p v-else>{{ randomJoke }}</p>
      </div>
      <div class="button-container">
        <button class="button" @click="getRandomJoke">Get a Random Joke</button>
      </div>
    </div>
  </div>
</template>

<script>/* eslint-disable */
  const config = {
    headers: {
      Accept: 'application/json'
    }
  }
  export default {
    head() {
      return {
        title: 'Dad Joke',
        meta: [
          {
            hid: 'description',
            name: 'description',
            content: 'Funny Dad Joke'
          }
        ]
      }
    },    
    data() {
      return {
        randomJoke: ''
      }
    },
    methods: {
      async getRandomJoke() {
        try {
          const response = await this.$axios.get('https://icanhazdadjoke.com/', config)
          this.randomJoke = response.data.joke
        } catch (error) {
          console.log(error.message)
        }
      }
    },
    async asyncData({ $axios, params }) {
      try {
        const response = await $axios.get('https://icanhazdadjoke.com/j/' + params.id, config)
      
        return {
          joke: response.data
        }        
      } catch (error) {
        console.log(error.message)
      }
    },
  }
</script>

<style scoped>
  .back-to-jokes {
    font-weight: bold;
    margin-bottom: 2rem;
  }
</style>