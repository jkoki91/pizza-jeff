<template>
  <div class="row align-items-start orders__container">
    <div v-if="response" class="todo__column d-flex align-items-center flex-column col-md-4 col-sm-12">
      <h1><span class="badge text-light ms-4">To do</span></h1>
      <ul id="example-1">
        <li v-for="item in response" :key="item.id">
          <order-card v-if="item.status===('CONFIRMED')" :orders="item"></order-card>
        </li>
      </ul>
    </div>
    <div v-if="response" class="inprocess__column d-flex align-items-center flex-column col-md-4 col-sm-12">
      <h1><span class="badge text-light ms-4">In progress</span></h1>
      <ul id="example-2">
        <li v-for="item in response" :key="item.id">
        <!-- Estp se debería poder hacer sin repetir código, pero no me coge el operador OR -->
          <order-card v-if="item.status===('IN_PROCESS')" :orders="item"></order-card>
          <order-card v-if="item.status===('IN_DELIVERY')" :orders="item"></order-card>
          <order-card v-if="item.status===('READY_TO_SERVE')" :orders="item"></order-card>
        </li>
      </ul>
    </div>
    <div v-if="response" class="done__column d-flex align-items-center flex-column col-md-4 col-sm-12">
      <h1><span class="badge text-light ms-4">Done</span></h1>      
      <ul id="example-3">
        <li v-for="item in response" :key="item.id"> 
        <!-- Estp se debería poder hacer sin repetir código, pero no me coge el operador OR -->
          <order-card v-if="item.status===('ABANDONED')" :orders="item"></order-card>
          <order-card v-if="item.status===('CANCELLED')" :orders="item"></order-card>
          <order-card v-if="item.status===('DELIVERED')" :orders="item"></order-card>
          <order-card v-if="item.status===('SERVED')" :orders="item"></order-card>
          <!-- <order-card v-if="item.status===('CANCELLED'||'DELIVERED'||'SERVED'||'ABANDONED')" :orders="item"></order-card> -->
        </li>
      </ul>
    </div>

  </div>
</template> 

<script>
import OrderCard from "./OrderCard.vue";

export default {
  components: {
    OrderCard,
  },
  data() {
    return {
      response: null,
      petition: this.getUsers(),
      orderedResponse: null,
    };
  },
  watch: {},
  methods: {
    async getUsers() {
      await fetch("http://localhost:1907/orders")
        .then((r) => r.json())
        .then((d) => {
          console.log("objeto", d.content);
          this.response = d.content;
          this.convertDate;
          // this.sortResponse
        });
    },
    sortResponse() {
      // console.log(this.response.sort(function(a, b){return a.scheduledDateInSeconds - b.scheduledDateInSeconds}))
      const sorted = () =>
        this.response.sort(function (a, b) {
          return a.scheduledDateInSeconds - b.scheduledDateInSeconds;
        });
      sorted();
      return { sorted };
    },
  },
  computed: {
    convertDate() {
      const hola = "hola";
      this.response.map((a) => {
        if (a.scheduledDate) {
          const splitedDate = a.scheduledDate.split("T");
          const day = splitedDate[0].split("-");
          const hour = splitedDate[1].split(":");
          const getTime = () => {
            //obtener la hora en segundos (seguramente se pueda hacer mejor)
            a.scheduledDateInSeconds =
              ((((parseInt(day[0]) - 1970) * 365.25 + parseInt(day[1])) * 30 +
                parseInt(day[2]) +
                parseInt(hour[0])) *
                60 +
                parseInt(hour[1])) *
                60 +
              parseInt(hour[2]);
          };
          getTime();
        } else {
          const splitedDate = a.requestedDate.split("T");
          const day = splitedDate[0].split("-");
          const hour = splitedDate[1].split(":");
          const getTime = () => {
            a.scheduledDateInSeconds =
              ((((parseInt(day[0]) - 1970) * 365.25 + parseInt(day[1])) * 30 +
                parseInt(day[2]) +
                parseInt(hour[0])) *
                60 +
                parseInt(hour[1])) *
                60 +
              parseInt(hour[2]);
          };
          getTime();
        }
      });
      this.sortResponse();
      return { hola };
    },
  },
};
</script>

<style scoped>
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