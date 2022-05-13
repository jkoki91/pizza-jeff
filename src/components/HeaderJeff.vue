<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-black">
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarTogglerDemo03" aria-controls="navbarTogglerDemo03" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>
  <a class="navbar-brand" href="#">
      <img class="logo__navbar" src="./../assets/logo-pizza-derret.png"/>
      <img class="logo__jeff" src="./../assets/logo-jeff.png" alt="Logo Jeff"/>
  </a>

  <div class="collapse navbar-collapse" id="navbarTogglerDemo03">
    <ul class="navbar-nav mr-auto mt-2 mt-lg-0">
      <li class="nav-item active">
        <a class="nav-link" href="#">Orders <span class="sr-only">(current)</span></a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">Historial</a>
      </li>
      <li class="nav-item">
        <a class="nav-link disabled">About PizzaJeff</a>
      </li>
    </ul>
    <form class="form-inline my-2 my-lg-0 mx-3">
      <input class="form-control mr-sm-2 ps-2" type="search" placeholder="Search an order" aria-label="Search">
      <button class="btn btn-outline-light my-2 my-sm-0" type="submit">Search</button>
    </form>
  </div>
</nav>
</template>

<script>

export default {

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

</style>