<script>
import AppAPI from './components/AppAPI.vue';
import AppHeader from './components/AppHeader.vue';
import AppMainVue from './components/AppMain.vue';
import axios from 'axios';

export default {
  data() {
    return {
      MoviesList: [],
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
    console.log('chiamata creata');
    this.getMovies()
    
  },
};
</script>

<template>
  
    <AppHeader />
    <AppMain :movies="MoviesList"/>
    <AppAPI @search="getMovies" />
    

</template>

<style scoped>

</style>
