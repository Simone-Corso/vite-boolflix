<script>
import AppAPI from './components/AppAPI.vue';
import AppHeader from './components/AppHeader.vue';
import AppMainVue from './components/AppMain.vue';


export default {
  components: {
    AppHeader,
    AppMainVue,
    AppAPI,
    
  },
};
</script>

<template>
  
    <AppHeader />
    <AppAPI />
    <AppMainVue />

</template>

<style scoped>

</style>
