<template lang="">
    <div>
       <input type="text" v-model="searchText">
       <button @click="$emit('search', searchText)"="searchMovies"> search

       </button>
    </div>
</template>
<script>
export default {
    name: 'AppSearch',

    data() {
        return {
            searchText: '',
            
        }
    },
}
</script>
<style lang="">
    
</style>