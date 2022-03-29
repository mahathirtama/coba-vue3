<template>
  <div>
    <navbar-vue />
    <div class="container">
        <form action="" v-on:submit.prevent="Update">
      <h1>Create Data</h1>
      <hr />

      <label for="namaProduct"><b>Nama Product</b></label>
      <input
        type="text"
        placeholder="Nama Product"
        name="namaProduct"
        v-model="dataEdit.nama"
        required
      />

      <label for="tipeProduct"><b>Tipe Product</b></label>
      <input
        type="text"
        placeholder="Tipe Product"
        name="tipeProduct"
        required
        v-model="dataEdit.kode"
      />

      <label for="harga"><b>Harga Product</b></label>
      <input type="number" placeholder="Harga Product" v-model="dataEdit.harga" name="harga" required />

      <hr />
      <button type="submit" class="registerbtn">Edit</button>
      </form>
    </div>
  </div>
</template>

<script>
import NavbarVue from "@/components/Navbar.vue";
import axios from "axios";
export default {
  name: "EditView",
  components: {
    NavbarVue,
  },
  data() {
    return {
        dataEdit: {}
    }
  },
  methods: {
    setData(data) {
      this.dataEdit = data
    },
    Update() {
        axios.put("http://localhost:3000/anime/" + this.dataEdit.id, this.dataEdit)
      .then(() => {
           this.$router.push({path: "/"})
        alert("Data Berhasil diubah")
      })
      .catch((err) => {
        console.log("gagal" + err);
      });
    }
  },
  mounted() {
    axios
      .get("http://localhost:3000/anime/" + this.$route.params.id)
      .then((res) => {
        this.setData(res.data);
      })
      .catch((err) => {
        console.log("gagal" + err);
      });
  },
};
</script>

<style scoped>
* {
  box-sizing: border-box;
}

/* Add padding to containers */
.container {
  padding: 16px;
}

/* Full-width input fields */
input[type="text"],
input[type="number"],
input[type="file"] {
  width: 100%;
  padding: 15px;
  margin: 5px 0 22px 0;
  display: inline-block;
  border: none;
  background: #f1f1f1;
}

input[type="text"]:focus,
input[type="number"]:focus,
input[type="file"]:focus {
  background-color: #ddd;
  outline: none;
}

/* Overwrite default styles of hr */
hr {
  border: 1px solid #f1f1f1;
  margin-bottom: 25px;
}

/* Set a style for the submit/register button */
.registerbtn {
  background-color: #04aa6d;
  color: white;
  padding: 16px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  width: 100%;
  opacity: 0.9;
}

.registerbtn:hover {
  opacity: 1;
}

/* Add a blue text color to links */
a {
  color: dodgerblue;
}

/* Set a grey background color and center the text of the "sign in" section */
</style>