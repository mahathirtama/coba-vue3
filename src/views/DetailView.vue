<template>
  <navbar-vue />
  <div class="container">
    <div class="row mt-5">
      <div class="col">
        <div class="card mb-3" style="max-width: 540px">
          <div class="row g-0">
            <div class="col-md-4">
              <img :src="'assets/image/' + products.gambar" class="img-fluid rounded-start" alt="..." />
            </div>
            <div class="col-md-8">
              <div class="card-body">
                <h5 class="card-title">Nama : {{ products.nama }}</h5>
                <p class="card-text">
                  Harga Rp. {{ products.harga }}
                </p>
                <p class="card-text">
                  <router-link class="btn btn-primary" :to="{name: 'home'}">Home</router-link>
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- <div class="row">
  <div class="column">
    <div class="card" >
        <img :src="'assets/image/' + products.gambar" alt="Avatar" style="width:200px">
        <div class="container">
          <h4><b>{{ products.nama }}</b></h4>
          <p>harga</p>
          <router-link class="edit" :to="{name: 'home'}">Home</router-link>
        </div>
      </div>
  </div>
</div> -->
</template>

<script>
import NavbarVue from "@/components/Navbar.vue";
import axios from "axios";
export default {
  name: "DetailView",
  components: {
    NavbarVue,
  },
  data() {
    return {
      products: [],
    };
  },
  mounted() {
    axios
      .get("http://localhost:3000/anime/" + this.$route.params.id)
      .then((res) => (this.products = res.data))
      .catch((err) => console.log(err));
  },
};
</script>

<style>
</style>