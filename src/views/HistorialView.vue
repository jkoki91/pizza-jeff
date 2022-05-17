<template>
  <div class="historial">
    <header-jeff></header-jeff>
    
    <footer-jeff></footer-jeff>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component'
import HeaderJeff from '../components/HeaderJeff.vue'
import FooterJeff from '../components/FooterJeff.vue'
// import image from '../assets/background_orange.jpg'
// import store from "../components/UsersOrders.vue"

// console.log('hola', store, 'hola')

@Options({
  components: {
    HeaderJeff,
    FooterJeff
  },
})
export default class HomeView extends Vue {}
</script>

<style scoped>
  .home__container{
    background-image: url('../assets/background_orange.jpg');
  }
</style>