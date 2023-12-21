<script>
import AppAPI from './components/AppAPI.vue';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import axios from 'axios';

export default {
  data() {
    return {
      MoviesList: [],
    }
  },

  methods: {
    getMovies(searchText) {
      console.log('chiamata creata');
      console.log(searchText);

    }
  },

  components: {
    AppMain,
    AppAPI,
  },

  created() {
    this.getMovies();
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
