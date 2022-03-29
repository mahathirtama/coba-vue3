<template>
  <NavBar />
  <div class="container">
    <table class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Nama</th>
          <th scope="col">Tipe</th>
          <th scope="col">Harga</th>
          <th scope="col">Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(data, index) in dataAsal" :key="data.id">
          <th scope="row">{{ index + 1 }}</th>
          <td>{{ data.namaProduct }}</td>
          <td>{{ data.tipeProduct }}</td>
          <td>Rp. {{ data.harga }}</td>
          <td>
            <button @click="Delete(data.id)" class="btn btn-danger">
              <i class="bi bi-trash"></i>
            </button>
          </td>
        </tr>
        <tr>
          <td align="right" colspan="3">
            <strong>Total Harga</strong>
          </td>
          <td>
            Rp. <strong>{{ totalHarga }}</strong>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import NavBar from "@/components/Navbar.vue";
import axios from "axios";
export default {
  name: "AboutView",
  components: {
    NavBar,
  },
  data() {
    return {
      dataAsal: [],
    };
  },
  methods: {
    Delete(id) {
      axios
        .delete("http://localhost:3000/keranjangs/" + id)
        .then(() => {
          this.$router.push({ path: "/" });
          alert("Berhasil Di Hapus");
        })
        .catch(() => {
          alert("Gagal di Hapus");
        });
    },
  },
  mounted() {
    axios
      .get("http://localhost:3000/keranjangs")
      .then((res) => {
        this.dataAsal = res.data;
      })
      .catch((err) => {
        console.log("Gagal" + err);
      });
  },
  computed: {
    totalHarga() {
      return this.dataAsal.reduce(function (items, data) {
        return items + data.harga;
      }, 0);
    },
  },
};
</script>

<style>
</style>
