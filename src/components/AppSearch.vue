<template>
  <header>
  <div class="search-bar">
    <h1>Boolflix</h1>
    <input type="text" v-model="searchText" @keyup.enter="search" @input="search" placeholder="Search" class="placeholder">
    <button @click="search">Search</button>
  </div>
  </header>
  <main>
  <div>
    <div v-if="ilRisultato">
      <div v-for="movie in moviesList" :key="movie.id" class="card">
        <img :src="movie.imageUrl" alt="Movie Poster">
        <div class="descrizione">
        <span>Titolo Originale: {{ movie.original_title }}</span><br>
        <span>Lingua:{{ movie.languageFlag }}</span><br>
        <span>Titolo: {{ movie.title }} </span><br>
        <span>Voto: {{ movie.vote_average }}</span><br>
        <span>Overview: {{ movie.overview }}</span>
      </div>
      </div>
    </div>
  </div>
</main>
</template>

<script>
import axios from 'axios';

const languageFlagMap = {
  en: '🇺🇸',
  es: '🇪🇸',
  fr: '🇫🇷',
  it: '🇮🇹'
  
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
            imageUrl: 'https://image.tmdb.org/t/p/w342/' + movie.poster_path,
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
            imageUrl: 'https://image.tmdb.org/t/p/w500/' + serie.poster_path,
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

h1{
  color: white;
}


.search-bar{
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: black;
  height: 75px;
}
.descrizione{
  transition: opacity 0.3s;
  width: 100%;
  opacity: 0;
}
.card{
  position: relative;
}

.card:hover .descrizione{
  opacity: 1;
  display: block;
}

</style>

