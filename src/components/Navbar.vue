<template>

 
    <nav class="navbar navbar-expand-lg bg-primary ">
      <div class="container">
  <a class="navbar-brand text-light ml-4" href="#" > <b-icon-droplet-half></b-icon-droplet-half> Perkopian</a>
 
  
  <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
    <div class="navbar-nav">
      <router-link class="nav-link text-light" to="/">Home</router-link>
      <router-link class="nav-link text-light" to="/menu">Menu</router-link>
    
    </div>
  </div>
  <span class="navbar-text mr-3">
     <router-link class="nav-link text-light "  to="/kerangjang">Keranjang

      <b-icon-bag></b-icon-bag>
      <span class="badge badge-success ml-2">0</span>
      </router-link>
    </span>
  
 </div>
</nav>
</template>

<script>
export default {
name : 'Navbar'
}
</script>

<style>




</style>