<template>
  <div>
    <input type="text" v-model="searchText" @keyup.enter="search" @input="search" placeholder="Search">
    <button @click="search">Search</button>
    <div v-if="ilRisultato">
      Risultati: {{ searchText }}
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      searchText: '',
      ilRisultato: false,
      moviesList: [],
    };
  },
  methods: {
    search() {
      this.$emit('search', this.searchText);

      axios.get('https://api.themoviedb.org/3/search/movie?api_key=86c594eddf3a5367752cf671fefca365&query=' + this.searchText)
        .then((response) => {
          console.log(response);
          this.moviesList = response.data.results;
          this.ilRisultato = true;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
  created() {
   
  },
};
</script>

<style scoped>
  
</style>


  