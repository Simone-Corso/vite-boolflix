<template lang="">
    <div>
       <input type="text" v-model="searchText">
       <button @click="$emit('search', searchText)" @keyup.enter="searchMovies"> search

       </button>
    </div>
</template>
<script>
export default {
    name: 'AppAPI',

    data() {
        return {
            searchText: '',
            
        }
    },
}
</script>
<style lang="">
    
</style>