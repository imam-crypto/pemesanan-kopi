<template>
<div class="div">
    <navbar/>
  <div class="container">
    <div class="row mt-4">
      <div class="col">
        <h2>Daftar Menu</h2>
      </div>
    </div>

      <div class="row-mt-3">
        <div class="col">
          <div class="input-group mt-3">
            <input
            v-model="search"
            type="text"
            class="form-control"
            placeholder="cari kopi"
            @keyup="searchKopi"
            />
            <div class="input-group-prepend">
              <span class="input-group-text" id="basic-addon1">
                <b-icon-search></b-icon-search>
              </span>
            </div>
          </div>
        </div>
      </div>


     <div class="row mb-3 mt-4">
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
import CardProduct from "@/components/CardProduct.vue"
import axios from "axios";

export default {
  name: "Menu",
  components: {
    Navbar,
    CardProduct,
  },
  data(){
    return {
      products:[],
      search:'',
    }
  },
  methods:{
    setProduct(data){
      this.products = data
    },
    searchKopi(){

  axios.get("http://localhost:3000/products?q="+this.search)
  .then(response =>
    this.setProduct(response.data)
  )
  .catch((error) => // handle error
    console.log(error));
       
    }
  },
   mounted(){
    axios.get("http://localhost:3000/products")
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