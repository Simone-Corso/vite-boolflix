<script>
import AppSearch from './components/AppSearch.vue';
import AppHeader from './components/AppMain.vue';
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
      const response = await axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: '86c594eddf3a5367752cf671fefca365',
          query: searchText,
        },
      });

      this.moviesList = response.data.results;
    } catch (error) {
      console.error('Error fetching movies:', error);
    }
  },
},
  components: {
    AppMain,
    AppSearch,
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
    <AppSearch @search="getMovies" />
  </div>
</template>
 

<style scoped>

</style>
