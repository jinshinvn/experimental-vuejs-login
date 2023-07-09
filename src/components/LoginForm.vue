
<template>
  <div>
    <h2>Login</h2>
    <form @submit.prevent="login">
      <div>
        <label for="email">Email:</label>
        <input type="email" id="email" v-model="email" required />
      </div>
      <div>
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="password" required autocomplete/>
      </div>
      <div>
        <button type="submit">Login</button>
      </div>
    </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      email: '',
      password: '',
    };
  },
  methods: {
    login() {
      axios.post('/api/login', {
        email: this.email,
        password: this.password,
      })
      // eslint-disable-next-line
      .then(response => {
        console.log('Logged in successfully');
      })
      .catch(error => {
        console.error('Login failed', error);
      });
    },
  },
};
</script>
