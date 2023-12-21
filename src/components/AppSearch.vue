
<template>
  <div>
    <input type="text" v-model="searchText" @input="search" placeholder="Search">
    <button @click="search">Search</button>
    <div v-if="ilRisultato">
  Risultati: {{ searchText }}
</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchText: '',
      ilRisultato: false,
    };
  },
  methods: {
    search() {
      
      this.$emit('search', this.searchText);
    },
  },
  created() {
    
  },
};
</script>

<style scoped>

</style>

  