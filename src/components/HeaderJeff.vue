<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-black">
  <button @click="showToggle()" class="navbar-toggler ms-3" type="button" data-toggle="collapse" data-target="#navbarTogglerDemo03" aria-controls="navbarTogglerDemo03" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon burguer__icon"></span>
  </button>
  <a class="navbar-brand" href="#">
      <img class="logo__navbar" src="./../assets/logo-pizza-derret.png"/>
      <img class="logo__jeff" src="./../assets/logo-jeff.png" alt="Logo Jeff"/>
  </a>
  <div class="collapse navbar-collapse" id="navbarTogglerDemo03">
    <ul class="navbar-nav mr-auto mt-2 mt-lg-0">
      <li class="nav-item active">
        <nav>
          <router-link class="nav-link link__header" to="/">Orders</router-link>
        </nav>
        <router-view/>
      </li>
      <li class="nav-item">
        <nav>
          <router-link class="nav-link link__header" to="/historial">Historial</router-link>
        </nav>
        <router-view/>
      </li>
      <li class="nav-item">
        <a class="nav-link disabled">About PizzaJeff</a>
      </li>
    </ul>
  </div>
  <form class="form-inline my-2 my-lg-0 mx-3" @submit="searchOrder">
      <input class="form-control mr-sm-2 ps-2" v-model="search" type="search" placeholder="Search an order" aria-label="Search">
      <button class="btn btn-outline-light my-2 my-sm-0" @click="$emit('search',this.search)" type="submit">Search</button>
  </form>
  </nav>
  <div v-if="visible" class="navbar-collapse d-flex justify-content-start px-5 pb-3 pt-2 mb-4 bg-black" style="width: fit-content; border-bottom-right-radius: 5px;" id="navbarTogglerDemo03">
    <ul class="navbar-nav mr-auto mt-2 mt-lg-0">
      <li class="nav-item">
        <nav>
          <router-link class="nav-link link__header" to="/">Orders</router-link>
        </nav>
        <router-view/>
      </li>
      <li class="nav-item">
        <nav>
          <router-link class="nav-link link__header" to="/historial">Historial</router-link>
        </nav>
        <router-view/>
      </li>
      <li class="nav-item">
        <a class="nav-link disabled">About PizzaJeff</a>
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  name:"HeaderJeff",
  emits: ["search"],
  methods:{
    showToggle() {
      this.visible?this.visible = false : this.visible = true
    },
    searchOrder(e){
      e.preventDefault()
    }
  },
  data() {
    return {
      visible: false,
      search:'',      
    }
  }
}
</script>

<style scoped>
*{
    margin: 0px;
    padding: 0px;
    box-sizing: border-box;
}

.logo__navbar{
    width: 8vh;
    margin: 2vh;
    margin-left: 5vh;
}
.logo__jeff{
    width: 15vh;
}

.link__header,li{
  color:white
}

.link__header:link {
  text-decoration: none;
  
}

.link__header:hover { 
  color: rgb(121, 118, 118); 
  text-decoration: none; 
  /* font-size: 1.2rem; */
  font-weight: bolder;
}

.link__header:visited {
  color: rgb(255, 255, 255);  
  font-family: arial; 
  text-decoration: none 
}

.burguer__icon:hover{
  /* font-weight: bolder; */
}


</style>