<script>
import AppAPI from './components/AppAPI.vue';
import AppHeader from './components/AppHeader.vue';
import AppMainVue from './components/AppMain.vue';
import axios from 'axios';

export default {
  data() {
    return {
      
    }
  },

  methods: {

    getMovies(searchText){

    }
    
  },

  components: {
    AppHeader,
    AppMainVue,
    AppAPI,
    axios,
    
  },

  created() {
    this.getMovies()
    
  },
};
</script>

<template>
  
    <AppHeader />
    <AppMainVue />
    <AppAPI />
    

</template>

<style scoped>

</style>
