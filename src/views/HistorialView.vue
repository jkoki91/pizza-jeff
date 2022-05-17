<template>
  <div class="historial home__container">
    <header-jeff></header-jeff>
    <div class="d-flex flex-direction-row justify-content-center align-items-center orders__container">
        <div v-if="response" class="todo__column d-flex align-items-center flex-column col-md-4 col-sm-12">
          <h1><span class="badge text-light ms-4">All orders</span></h1>
          <ul id="example-1">
              <li v-for="item in response" :key="item.id">
              <order-card :orders="item"></order-card>
            </li>
          </ul>
        </div>
    </div>
    <footer-jeff></footer-jeff>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component'
import HeaderJeff from '../components/HeaderJeff.vue'
import FooterJeff from '../components/FooterJeff.vue'
import OrderCard from "../components/OrderCard.vue";



@Options({
  components: {
    HeaderJeff,
    OrderCard,
    FooterJeff
  },
  data() {
    return {
      allOrders: localStorage.getItem('allOrders'),
      getAllOrders: this.beforeMount,
      response:null
    }
  },
  methods:{
      getOrders(){
          console.log('ver storage', JSON.parse(this.allOrders))
          this.response = JSON.parse(this.allOrders)
      }
  },
  beforeMount(){
    this.getOrders()
 }
})


export default class HomeView extends Vue {}
</script>

<style scoped>
.home__container{
    background-image: url('../assets/background_orange.jpg');
}

.orders__container{
  min-width: fit-content;
  padding-right: 4vw;
}

li {
  list-style: none;
}

span{
  background-color: rgb(228, 117, 66);
  margin-top: 5vh;
  box-shadow: 5px 5px 24px 1px rgba(0,0,0,0.87);

}


</style>