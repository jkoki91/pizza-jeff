<template>
  <div class="card card__container my-3" :id="ordersInfo.status" style="width: 18rem">
    <div class="card-body card__body">
      <h5 class="card-title card__title">
        Order number {{ ordersInfo.number }} for
        {{ ordersInfo.customer.customerName }}
      </h5>
      <p class="m-1">Products:</p>
      <ul v-if="products" class="d-flex flex-column justify-content-center align-items-center" id="products-list">
        <li v-for="product in products" :key="product.id">
          <img class="img__product" src="../assets/circle-pizza.png" alt="">
          {{ product }}
        </li>
      </ul>
      <div class="d-flex flex-row justify-content-around mt-1">
        <button v-if="!visibleDetails" @click="showDetails()" class="btn dropdown-toggle">Details</button>
        <button v-if="visibleDetails" @click="showDetails()" class="btn dropdown-toggle">Less details</button>
        <button class="btn btn-primary client__button" @click="showModal()">Client info</button>
      </div>
      <div  v-if="visibleDetails">
      <div class="">
          <div class="dropdown">
            <div class="d-flex flex-direction-row align-items-center justify-content-center">
                <p class="mt-3">Status: </p>
                <a @click="showStatus()" class="btn dropdown-toggle" id="status__dropdown">
                    {{ ordersInfo.status }}
                </a>
            </div>
          <ul  v-if="visibleStatus" aria-labelledby="dropdownMenuButton1">
                <li v-for="statusOrder in statusP" :key="statusOrder"> 
                    <button @click="closeStatus(statusOrder,ordersInfo.id)" class="dropdown-item" id="status__dropdown">{{statusOrder}}</button>
                </li>

                <!-- <li><button @click="closeStatus('CONFIRMED',ordersInfo.id)" class="dropdown-item" id="status__dropdown">CONFIRMED</button></li>
                <li><button @click="closeStatus('IN_PROCESS',ordersInfo.id)" class="dropdown-item" id="status__dropdown">IN_PROCESS</button></li>
                <li><button @click="closeStatus('CANCELLED',ordersInfo.id)" class="dropdown-item" id="status__dropdown">CANCELLED</button></li>
                <li><button @click="closeStatus('DELIVERED',ordersInfo.id)" class="dropdown-item" id="status__dropdown">DELIVERED</button></li>
                <li><button @click="closeStatus('READY_TO_SERVE',ordersInfo.id)" class="dropdown-item" id="status__dropdown">READY_TO_SERVE</button></li>
                <li><button @click="closeStatus('SERVED',ordersInfo.id)" class="dropdown-item" id="status__dropdown">SERVED</button></li>
                <li><button @click="closeStatus('IN_DELIVERY',ordersInfo.id)" class="dropdown-item" id="status__dropdown">IN_DELIVERY</button></li>
                <li><button @click="closeStatus('ABANDONED',ordersInfo.id)" class="dropdown-item" id="status__dropdown">ABANDONED</button></li> -->
          </ul>
        </div>
      </div>
        <p class="card-text">Reception type: {{ ordersInfo.receptionType }}</p>
        <p class="card-text">Schedule hour: {{ ordersInfo.scheduledDate || "ASAP" }}</p>
      </div>
    </div>
    <user-info :visible="visible" :customerInfo="customerInfo" @closeFun="closeModal"></user-info>
  </div>
</template>

<script>
import { Options, Vue } from "vue-class-component";   
import UserInfo from "./UserInfo.vue";

@Options({
  components: {
    UserInfo,
  },
  props: {
    orders: Object,
  },
  methods: {
    seeProducts() {
      this.products = this.orders.products.map((a) => a.productName);
    },
    showModal() {
      this.visible = true
    },
    closeModal() {
      this.visible = false
    },
    showDetails() {
      this.visibleDetails?this.visibleDetails = false :this.visibleDetails = true
    },
    showStatus() {
      this.visibleStatus? this.visibleStatus = false : this.visibleStatus = true
    },
    closeStatus(value,id) {
      const data = {
          status: value
      }  
      console.log(id)
      fetch(`http://localhost:1907/orders/${id}`,{
            method: 'POST',
            body: JSON.stringify(data),
            headers: { 'Content-Type': 'application/json' }
        })
      this.ordersInfo.status = value   
      this.visibleStatus = false
    },
  },
  data() {
    return {
      probando: this.seeProducts(),
      ordersInfo: this.orders,
      poducts: null,
      visible: false,
      visibleDetails: false,
      visibleStatus: false,
      customerInfo: this.orders.customer,
      statusP:['CONFIRMED','IN_PROCESS','CANCELLED','DELIVERED','READY_TO_SERVE','SERVED','IN_DELIVERY','ABANDONED'],
    }
  },
})
export default class OrderCard extends Vue {}
</script>

<style scoped>
*{
    font-size: small;
}
.card__container{
    min-width: fit-content;
    max-width: 30vw;
    box-shadow: 5px 5px 24px 1px rgba(0,0,0,0.87);
}

#CANCELLED,#ABANDONED{
    background: rgb(255, 178, 178);
}

#DELIVERED,#READY_TO_SERVE,#SERVED{
    background: rgb(173, 251, 172);
}
#IN_PROCESS,#IN_DELIVERY{
    background: rgb(251, 255, 178);
}

.card__title{
    font-weight: bold;
    margin-top: 8px;
}

#products-list{
    padding: 0px;
}

li {
  list-style: none;
}

.img__product{
    max-width: 15px;
}

.butt__style{
    width: 5rem;
}

#status__dropdown{
    border: none;
    user-select: none;
    font-size: x-small;
}

.client__button{
    background-color: rgb(228, 117, 66);
    border: none;
    font-size: x-small;
    padding: 0.3rem;
    height: fit-content;
    margin-top: 0.5rem;
}

@media screen and (min-width: 0px) and (max-width: 768px){
    .card__container{
        min-width: 60vw;
    }
}

</style>