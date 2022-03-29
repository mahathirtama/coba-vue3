<template>
  <div class="home">
    <NavBar />
    <div class="container">
       <div class="row md-3">
        <div class="col-md-4 mt-4" v-bind:key="product.id" v-for="product in products">
          <CardView :product="product" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import NavBar from '@/components/Navbar.vue'
import CardView from '@/components/CardView.vue'
import axios from 'axios';

export default {
  name: 'HomeView',
  components: {
    NavBar,
    CardView
  },
  data() {
    return {
      products: []
    }
  },
  mounted() {
    
    axios.get('http://localhost:3000/anime')
    .then(res => this.products = res.data)
    .catch(err => console.log(err));
  }
}
</script>
