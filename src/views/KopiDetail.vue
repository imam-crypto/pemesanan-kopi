<template>
  <div class="KopiDetail">
      <navbar />
      <div class="container my-4">
          <div class="row">
              <div class="col">
                  <nav aria-label="breadcrumb">
                     <ol class="breadcrumb">
                         <li class="breadcrumb-item">
                             <router-link to="/" class="text-info">Home</router-link>
                         </li>
                         <li class="breadcrumb-item">
                             <router-link to="/menu" class="text-info">Menu</router-link>
                         </li> 
                         <li class="breadcrumb-item active" aria-current="page">Pesan Kopi</li>
                     </ol>
                  </nav>
              </div>
          </div>

          <div class="row">
              <div class="col-md-6">
                  <img :src="'../image/' + product.gambar" class="img-fluid shadow" alt="gambarKopi">
              </div>
              <div class="col-md-6">
                  <h4> {{product.nama}} </h4>
                  <hr>
                  <h4>Rp.  {{product.harga}} </h4>
                  <hr>
                   <form class="mt-4">
                       <div class="form-group">
                           <label>Jumlah Pesanan</label>
                           <input type="number" class="form-control" v-model="pesan.jumlah_pemesanan"/>
                       </div>
                       <div class="form-group">
                           <label>Keterangan</label>
                           <textarea v-model="pesan.keterangan" type="text" class="form-control" placeholder="campuran creams "></textarea>
                       </div>
                       <button type="submit" class="btn btn-warning" @click="pemesanan"> <b-icon-list></b-icon-list> Pesan</button>
                       </form> 
              </div>
          </div>
      </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import axios from "axios";
export default {
  name: "KopiDetail",
  components: {
    Navbar,
  },
  data(){
      return{
          product:{}
      }
  },
  methods:{
      setProduct(data){
          this.product=data
      },
      pemesanan(){
          this.pesan.products = this.product;
           axios
           .post("http://localhost:3000/keranjangs/" , this.pesan)
            .then(()=>{
                console.log("berhasil");
            })
            .catch((err) => console.log(err))
      }
  },
    mounted(){
    axios.get("http://localhost:3000/products/"+this.$route.params.id)
  .then(response =>
    this.setProduct(response.data)
  )
  .catch((error) => // handle error
    console.log(error));
  
  }
};
</script>

<style>
</style>