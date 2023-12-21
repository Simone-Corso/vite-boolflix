
<template>
  <div>
    <AppHeader />
    <AppMain :movies="moviesList"/>
    <AppSearch @search="getMovies" />
  </div>
</template>

<script>
import AppSearch from './components/AppSearch.vue';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';

export default {
  data() {
    return {
      moviesList: [],
    };
  },
  methods: {
    getMovies(searchText) {
      console.log('chiamata', searchText);
    },
  },
  components: {
    AppSearch,
    AppMain,
    AppHeader,
  },
  created() {
    
  },
};
</script>

<style scoped>

</style>
