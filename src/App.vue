<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer">
      <!--  -->
    </v-navigation-drawer>

    <v-app-bar>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-app-bar-title>List</v-app-bar-title>
    </v-app-bar>

    <v-main>
      <HomeView/>

    </v-main>
  </v-app>
</template>

<script setup>  
  import { ref } from 'vue'
import HomeView from './views/HomeView.vue';

  const drawer = ref(null)
</script>

<script>
  export default {
    data: () => ({ drawer: null }),
  }
</script>