<script setup>
import { RouterView } from 'vue-router'
//import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue';

</script>

<template>
  <Footer v-if="$route.name === 'gallery'"></Footer>
  <Header v-else></Header>
  <RouterView />
</template>

