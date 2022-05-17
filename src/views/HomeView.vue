<template>
  <div class="home home__container">
    <header-jeff></header-jeff>
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
      <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <users-orders></users-orders>
    <footer-jeff></footer-jeff>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src
import UsersOrders from '@/components/UsersOrders.vue'
import HeaderJeff from '../components/HeaderJeff.vue'
import FooterJeff from '../components/FooterJeff.vue'
// import image from '../assets/background_orange.jpg'


@Options({
  components: {
    HelloWorld,
    UsersOrders,
    HeaderJeff,
    FooterJeff
  },
})
export default class HomeView extends Vue {}
</script>

<style scoped>
  .home__container{
    background-image: url('../assets/background_orange.jpg');
    /* background-color: brown; */
  }
</style>