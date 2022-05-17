<template>
  <div class="home home__container">
    <header-jeff @search="searchOrder"></header-jeff>
    <users-orders :searchedOrder="searchedOrder1" :key="searchedOrder1"></users-orders>
    <footer-jeff></footer-jeff>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import UsersOrders from '@/components/UsersOrders.vue'
import HeaderJeff from '../components/HeaderJeff.vue'
import FooterJeff from '../components/FooterJeff.vue'


@Options({
  data() {
    return {
      searchedOrder1: '',
    };
  },
  components: {
    UsersOrders,
    HeaderJeff,
    FooterJeff
  },
  methods:{
    searchOrder(info:string){ //pendiente hacer filtro
      console.log('Desde home',info)
      // return this.searchedOrder1 = info
    }
  }
})
export default class HomeView extends Vue {}
</script>

<style scoped>
  .home__container{
    background-image: url('../assets/background_orange.jpg');
  }
</style>