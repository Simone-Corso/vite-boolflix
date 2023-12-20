<script>
import AppAPI from './components/AppAPI.vue';
import AppHeader from './components/AppHeader.vue';
import AppMainVue from './components/AppMain.vue';


export default {
  components: {
    AppAPI,
    AppHeader,
    AppMainVue,
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
