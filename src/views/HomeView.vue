<template>
  <div class="home">
    <HeaderJeff></HeaderJeff>
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
      <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <UsersOrders></UsersOrders>
    <footer-jeff></footer-jeff>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src
import UsersOrders from '@/components/UsersOrders.vue'
import HeaderJeff from '../components/HeaderJeff.vue'
import FooterJeff from '../components/FooterJeff.vue'


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
