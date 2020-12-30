<template>
  <div class="input-container">
    <input type="text" placeholder="Search jokes..." @input="handleSearch">
  </div>
</template>

<script>/* eslint-disable */
  export default {
    name: 'SearchJokes',
    methods: {
      handleSearch(event) {
        this.$emit('search', event.target.value)
      }
    }
  }
</script>

<style scoped>
  input {
    border: 1px dotted #ccc;
    padding: .5rem 1rem;
  }
  @media (max-width: 767px) {
    .input-container,
    input {
      width: 100%;
    }    
  }
</style>