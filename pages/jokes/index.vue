<template>
  <div class="page-content">
    <div class="container">
      <div class="flex-container">
        <h1>Dad jokes</h1>
        <SearchJokes @search="setSearchText" />
      </div>
      <ul class="jokes-list">
        <Joke v-for="joke in filteredJokes" :key="joke.id" :joke="joke" />
      </ul>
      <div v-if="!filteredJokes.length" class="text-center mt-1 no-jokes-box">
        <p>No jokes to display</p>
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
    name: 'Jokes',
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
    data() {
      return {
        searchText: ''
      }
    },
    methods: {
      setSearchText(searchText) {
        this.searchText = searchText
      }
    },
    computed: {
      filteredJokes() {
        return this.jokes.filter(joke => {
          return joke.joke.includes(this.searchText)
        })
      }
    },
    async asyncData({ $axios, error }) {
      try {
        const response = await $axios.get('https://icanhazdadjoke.com/search', config)
      
        return {
          jokes: response.data.results
        }        
      } catch (e) {
        error(e)       
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
  .flex-container {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .no-jokes-box {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 1rem;
    border: 1px dotted #ccc;
  }

  @media (max-width: 767px) {
    .flex-container {
      flex-direction: column;
      align-items: flex-start;
    }
    .flex-container h1 {
      margin-bottom: 1rem;
    }
  }
</style>