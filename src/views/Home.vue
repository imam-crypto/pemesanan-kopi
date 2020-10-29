<template>
  <div class="home">
   <navbar/>
   
   <div class="container">
     <!-- <header/> -->
     <Hero/>


  <div class="row mt-4">
  <div class="col">
  <h3>Kopi <strong>Terbaik</strong></h3>  
  </div>
  <div class="col">
  <router-link to="/menu" class="btn btn-warning float-right"> Lihat Lebih</router-link>
  </div>
  </div>

  <div class="row my-3">
    <div class="col-md-4" v-for="product in products" :key="product.id">
      <CardProduct :product="product"/>
    </div>
  </div>


   </div>



  </div>
</template>

<script>
// @ is an alias to /src
import Navbar from "@/components/Navbar.vue";
// import Header from "@/components/Header.vue";
import Hero from "@/components/Hero.vue";
import CardProduct from "@/components/CardProduct.vue"
import axios from "axios";

export default {
  name: "Home",
  components: {
    Navbar,
    // Header,
    Hero,
    CardProduct,
  },
  data(){
    return {
      products:[]
    }
  },
  methods:{
    setProduct(data){
      this.products = data
    }
  },

  mounted(){
    axios.get("http://localhost:3000/best-kopis")
  .then(response =>
    this.setProduct(response.data)
  )
  .catch((error) => // handle error
    console.log(error));
  
  }

};
</script>
