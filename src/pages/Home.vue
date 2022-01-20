<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div v-for="(user,index) in users " :key="index">
      <table class="table">
        <thead>
        <tr>
          <th scope="col">id</th>
          <th scope="col">name</th>
          <th scope="col">email</th>
        </tr>
        </thead>
        <tbody>
        <tr>
          <th scope="row">{{ index+1 }}</th>
          <td>{{ user.name }}</td>
          <td>{{user.email}}</td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>

import axios from "axios"

export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: "users",
      users: [],
    }
  },
  created(){
    axios.get('http://store.loc/api/users')
        .then(function( response ){
          this.users = response.data;
        }.bind(this));
  }
}
</script>

