<template>
  <div class="home">
    <form action="#" method="post" @submit.prevent="login">
      <div>
        <input type="email" name="email" placeholder="email">
      </div>
      <div>
        <input type="password" name="password" placeholder="password">
      </div>
      <div>
        <button type="submit">Login</button>
      </div>
    </form>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'

axios.defaults.withCredentials = true;
axios.defaults.baseURL = 'http://localhost:8000'
export default {
  name: 'Home',
  methods: {
    login() {
      axios.get('/sanctum/csrf-cookie').then(response => {
         axios.post('/login', {
           email:'xiajun@1234.com',
           password:'12345678'
         })
         .then(response => {
           this.$router.push({ name: 'Dashboard' })
         })
      });
    }
  },
}
</script>
