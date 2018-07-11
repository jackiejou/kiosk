<template>
  <div id="modal" class="signup">
    <h2>
      Register
    </h2>
    <form v-on:submit="register">
      <input type="text" placeholder="First Name" v-model="newUser.firstName">
      <br>
      <input type="text" placeholder="Last Name" v-model="newUser.lastName">
      <br>
      <input type="email" placeholder="Email" v-model="newUser.email">
      <br>
      <input type="submit" value="Submit"> {{ msg }}
    </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'signup',
  data() {
    return  {
      newUser: {},
      msg: '',
    }
  },
  methods: {
    register: function (e) {
      console.log(this.newUser.firstName, this.newUser.lastName, this.newUser.email);
      let temp = this;
      axios
        .get('https://jsonplaceholder.typicode.com/users')
        .then(function(response) {
          console.log(response.data);
          temp.msg = 'Registered successfully!';
        });
      e.preventDefault();
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.signup {

}
</style>
