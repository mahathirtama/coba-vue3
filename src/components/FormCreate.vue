<template>
  <form  @submit.prevent="handleSubmit">
  <div class="container">
    <h1>Create Data</h1>
    <hr>
    <label for="namaProduct"><b>Nama Product</b></label>
    <input type="text" placeholder="Nama Product" v-model="dataBaru.namaProduct" name="namaProduct" required>

    <label for="tipeProduct"><b>Tipe Product</b></label>
    <input type="text" placeholder="Tipe Product" v-model="dataBaru.tipeProduct" name="tipeProduct" required>
    
    <label for="harga"><b>Harga Product</b></label>
    <input type="number" placeholder="Harga Product" v-model="dataBaru.harga" name="harga" required>

    <hr>
    <button type="submit" value="submit" class="registerbtn">Create</button>
  </div>
</form>
</template>

<script>
import axios from 'axios'
export default {
    name: 'FormCreate',
    data() {
      return {
        dataBaru: {}
      }
    },
    methods: {
      handleSubmit() {
        axios.post('http://localhost:3000/keranjangs', this.dataBaru).then(() => {
          this.$router.push({path: "/about"})
          alert('Berhasil Di Tambahkan')
        }).catch(() => {
          alert("Gagal Di Tambahkan")
        });
      }
    }
}
</script>

<style scoped>
* {box-sizing: border-box}

/* Add padding to containers */
.container {
  padding: 16px;
}

/* Full-width input fields */
input[type=text], input[type=number], input[type=file] {
  width: 100%;
  padding: 15px;
  margin: 5px 0 22px 0;
  display: inline-block;
  border: none;
  background: #f1f1f1;
}

input[type=text]:focus, input[type=number]:focus, input[type=file]:focus {
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
  background-color: #04AA6D;
  color: white;
  padding: 16px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  width: 100%;
  opacity: 0.9;
}

.registerbtn:hover {
  opacity:1;
}

/* Add a blue text color to links */
a {
  color: dodgerblue;
}

/* Set a grey background color and center the text of the "sign in" section */
.signin {
  background-color: #f1f1f1;
  text-align: center;
}
</style>