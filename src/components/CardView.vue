<template>
  <div class="card" style="width: 18rem">
    <img
      :src="'assets/image/' + product.gambar"
      class="card-img-top"
      style="height: 200px"
    />
    <div class="card-body">
      <h5 class="card-title"> Nama: {{ product.nama }}</h5>
      <p class="card-text">
        Harga Rp. {{ product.harga }}
      </p>
      <div class="row md-2">
        <div class="col md-6">
          <router-link
          class="btn btn-warning"
          :to="{ name: 'edit', params: { id: product.id } }"
          >Edit</router-link
        >
        </div>
        <div class="col md-6">
          <router-link
          class="btn btn-success"
          :to="{ name: 'detail', params: { id: product.id } }"
          >Detail</router-link
        >
        </div>
      </div>
    </div>
  </div>

  <!-- <div class="row">
  <div class="column">
    <div class="card" >
        <img :src="'assets/image/' + product.gambar" alt="Avatar" style="width:200px">
        <div class="container">
          <h4><b>{{ product.namaItem }}</b></h4>
          <p>{{ product.harga }}</p>
          <router-link class="edit" :to="{name: 'edit', params: {id: product.id}}">Edit</router-link>
          <router-link class="detail" :to="{name: 'detail', params: {id: product.id}}">Detail</router-link>
          <a href="" class="delete">Delete</a>
        </div>
      </div>
  </div>
</div> -->
</template>

<script>
export default {
  name: "CardView",
  props: ["product"],
};
</script>

<style scoped>
</style>