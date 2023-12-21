<template>
  <div>
    <input type="text" v-model="searchText" @keyup.enter="search" @input="search" placeholder="Search">
    <button @click="search">Search</button>
    <div v-if="ilRisultato">
      <div v-for="movie in moviesList" :key="movie.id">
        <img :src="movie.imageUrl" alt="Movie Poster">
        {{ movie.original_title }} {{ movie.languageFlag }}
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

const languageFlagMap = {
  en: '🇺🇸',
  es: '🇪🇸',
  fr: '🇫🇷',
};

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
          this.moviesList = response.data.results.map((movie) => ({
            ...movie,
            languageFlag: this.getLanguageFlag(movie.original_language),
          }));
          this.ilRisultato = true;
        })
        .catch((error) => {
          console.log(error);
        });

      
      axios.get('https://api.themoviedb.org/3/search/tv?api_key=86c594eddf3a5367752cf671fefca365&query=' + this.searchText)
        .then((response) => {
          console.log(response);
          
          this.moviesList = this.moviesList.concat(response.data.results.map((serie) => ({
            ...serie,
            languageFlag: this.getLanguageFlag(serie.original_language),
          })));
          this.ilRisultato = true;
        })
        .catch((error) => {
          console.log(error);
        });
    },

    getLanguageFlag(language) {
      return languageFlagMap[language] || '';
    },
  },
};
</script>

<style scoped>

.search{
display: flex;
justify-content: center;
align-items: center;
flex-wrap: wrap;
}

</style>


  