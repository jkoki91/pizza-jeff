<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
      <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <UsersOrders></UsersOrders>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src
import UsersOrders from '@/components/UsersOrders.vue'


@Options({
  components: {
    HelloWorld,
    UsersOrders

  },
})
export default class HomeView extends Vue {}
</script>
