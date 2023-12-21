<script>
import AppAPI from './components/AppAPI.vue';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import axios from 'axios';

export default {
  data() {
    return {
      moviesList: [],
    }
  },

  methods: {
    async getMovies(searchText) {
      try {
        
        const response = await axios.get(`${searchText}`);
        
        
        this.moviesList = response.data.results;
      } catch (error) {
        console.error('Error fetching movies:', error);
      }
    }
  },

  components: {
    AppMain,
    AppAPI,
    AppHeader,
  },

  created() {
    
    this.getMovies('');
  },
};
</script>

<template>
  <div>
    <AppHeader />
    <AppMain :movies="moviesList"/>
    <AppAPI @search="getMovies" />
  </div>
</template>

<style scoped>

</style>
