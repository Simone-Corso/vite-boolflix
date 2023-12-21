<template lang="">
    <div>
      <input type="text" v-model="searchText">
      <button @click="search">search</button>

    </div>
  </template>
  <script>
  export default {
    name: 'AppSearch',
  
    data() {
      return {
        searchText: '',
      }
    },
  
    methods: {
      search() {
        this.$emit('search', this.searchText);
      }
    },
  }
  </script>
  <style lang="">
    
  </style>
  