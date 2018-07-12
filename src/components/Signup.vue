<template>
  <div>
    <button id="button" v-on:click="showModal">Sign Up</button>
    <div id="modal" v-if="show">
      <form id="modal-content" v-on:submit="register">
        <span v-on:click="close" id="close" title="Close Modal">&times;</span>
        <h2>
          Sign Up
        </h2>
        <input type="text" placeholder="First Name" v-model="newUser.firstName">
        <br>
        <input type="text" placeholder="Last Name" v-model="newUser.lastName">
        <br>
        <input type="email" placeholder="Email" v-model="newUser.email">
        <br>
        <input type="submit" value="Submit">
        <br>
        <p>{{ msg }}</p>
      </form>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'signup',
  data() {
    return  {
      show: false,
      newUser: {},
      msg: '',
    }
  },
  methods: {
    showModal: function() {
      this.show = true;
    },
    register: function (e) {
      console.log(this.newUser.firstName, this.newUser.lastName, this.newUser.email);
      let temp = this;
      axios
        .get('https://jsonplaceholder.typicode.com/users')
        .then(function(response) {
          console.log(response.data);
          temp.msg = 'Signed up successfully!';
        });
      e.preventDefault();
    },
    close: function () {
      this.show = false;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#button {
  background-color: lightcoral;
  top: 40%;
  left: 45%;
  position: absolute;
  width: 10%;
  height:50px;
  border: none;
  border-radius: 5px;
  color: white;
  margin: auto;
  box-shadow: 5px 5px 5px grey;
}

#button:hover{
  background-color: white;
  color: lightcoral;
  font-weight: bold;
  cursor: pointer;
}

#modal {
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgba(0,0,0,0.4);
  padding-top: 60px;
}

#modal-content {
  background-color: #fefefe;
  margin: auto;
  border: 1px solid lightslategrey;
  width: 20%;
  height: 30%;
  padding: 10px;
}

#close {
  font-size: 50px;
  top: 0;
  right: 30px;
  position: absolute;
  color:white;
}

#close:hover {
  color: red;
  cursor: pointer;
}

input {
  margin: 5px;
}

input[type=text], [type=email] {
  border: 3px solid #555;
  padding: 5px;
}

input:focus[type=text], :focus[type=email] {
  background-color: aliceblue;
  border: 3px solid #555;
}

input[type=submit] {
  border: none;
  padding: 5px 15px;
  color: white;
  margin-top: 15px;
  background-color: deepskyblue;
  box-shadow: 2px 2px 5px grey;
  cursor: pointer;
}

input:hover[type=submit] {

}

p {
  color:green;
}
</style>
