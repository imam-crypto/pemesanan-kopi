<template>
    <div class="card shadow card-product my-2" >
         <img :src="'image/' + product.gambar" class="img-fluid" alt="Kopi" height="400px" width="450px">
  <div class="card-body">
    <h5 class="card-title">{{product.nama}}</h5>
    <p class="card-text">Harga : <strong> Rp.{{product.harga}}</strong> </p>
    <router-link :to="'/menu/'+product.id" class="btn btn-primary"> <b-icon-cart></b-icon-cart> Pesan</router-link>
  </div>
</div>
</template>

<script>
export default {
    name:'CardProduct',
    props:['product']

}
</script>

<style>

</style>