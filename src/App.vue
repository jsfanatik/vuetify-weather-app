<template>
  <v-app id="inspire">
    <SearchBar />
    <router-view />
  </v-app>
</template>

<script setup>
  import SearchBar from './components/SearchBar.vue';
</script>
