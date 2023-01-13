
<template>
  <!-- event.preventDefault = .prevent  -->
  <form v-on:submit.prevent="submitForm">
    <div>
      <label for="username">id:</label>
      <input id="username" type="text" v-model="username">
    </div>
    <div>
      <label for="userpw">pw:</label>
      <input id="userpw" type="password" v-model="password">
    </div>
    <button type="submit">login</button>
  </form>  
</template>

<script>

import axios from 'axios';

export default {
  data: function() {
    return {
      username: '',
      password: '',
    }
  },
  methods: {
    submitForm: function() {
      
      var url = 'https://jsonplaceholder.typicode.com/users';
      var data = {
        username : this.username,
        password : this.password
      };
      axios.post(url, data)
        .then(function(response) {
            console.log('resp',response);
        })

        .catch(function(error) {
            console.log('error',error)
        })
    }
  }
}
</script>

<style>

</style>