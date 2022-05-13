<template>
  <div>
    <h1 class="bg-primary text-white text-center p-2">Probando Orders</h1>

    <button class="btn btn-primary">Hola Mundo</button>

    <div class="card" style="width: 18rem">
      <!-- <img src="..." class="card-img-top" alt="..." /> -->
      <div class="card-body">
        <h5 class="card-title">Card title</h5>
        <p class="card-text">
          Some quick example text to build on the card title and make up the
          bulk of the card's content.
        </p>
        <a href="#" class="btn btn-primary">Go somewhere</a>
      </div>
    </div>

    <!-- <ul id="example-1">
      <li v-for="item in response" :key="item.id">
        <div>
            <p>Number: {{ item.number }}</p>
            <p>Status: {{ item.status }}</p>
            <p>Type: {{ item.type }}</p>
            <p>Reception Type: {{ item.receptionType }}</p>
            <p>Customer: {{ item.customer }}</p>
            <p>Products: {{ item.products }}</p>
        </div>
      </li>
    </ul> -->
  </div>
</template>

<script>

export default {
  data() {
    return {
      response: null,
      content: this.getUsers(),
    };
  },
  watch: {},
  methods: {
    async getUsers() {
      await fetch("http://localhost:1907/orders")
        .then((r) => r.json())
        .then((d) => {
          console.log(d.content);
          this.response = d.content;
        });
    },
  },
  computed: {
    // content: this.getUsers()
  },
};
</script>

<style>
</style>