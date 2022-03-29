<template>
  <form  @submit.prevent="handleSubmit">
  <div class="container">
    <h1>Register</h1>
    <p>Please fill in this form to create an account.</p>
    <hr>

    <label for="nama"><b>Nama Lengkap</b></label>
    <input type="text" placeholder="Nama Lengkap" v-model="nama" name="nama" required>

    <label for="email"><b>Email</b></label>
    <input type="text" placeholder="Email" v-model="email" name="email" required>

    <label for="tglLahir"><b>Tanggal Lahir</b></label>
    <input type="text" placeholder="Tanggal Lahir" v-model="tglLahir" name="tglLahir" required>
    
    <label for="username"><b>Username</b></label>
    <input type="text" placeholder="Username" v-model="username" name="username" required>

    <label for="pws"><b>Password</b></label>
    <input type="password" placeholder="Password" v-model="password" name="password" required>

    <hr>
    <button type="submit" value="submit" class="registerbtn">Register</button>
  </div>
</form>
    <div class="container signin">
    <p>Already have an account? <a href="/login">Sign in</a>.</p>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'RegisterView',
    data() {
        return {
            nama: '',
            email: '',
            tglLahir: '',
            username: '',
            password: '',
        }
    },
    methods: {
        async handleSubmit() {
            // const response = await axios.post('http://localhost:8080/uasmobAPI/api/register.php', {
            // nama: this.nama,
            // email: this.email,
            // tglLahir: this.tglLahir,
            // username: this.username,
            // password: this.password,

            // })
            // console.log(response)
            // this.$router.push('/login')

            const data = {
                nama: this.nama,
                email: this.email,
                tglLahir: this.tglLahir,
                username: this.username,
                password: this.password
            }
            axios.post('http://localhost:8080/uasmobAPI/api/register.php', data)
            .then(
                res => {
                    console.log(res)
                }
            ).catch(
                err => {
                    console.log(err)
                }
            )
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
input[type=text], input[type=password] {
  width: 100%;
  padding: 15px;
  margin: 5px 0 22px 0;
  display: inline-block;
  border: none;
  background: #f1f1f1;
}

input[type=text]:focus, input[type=password]:focus {
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