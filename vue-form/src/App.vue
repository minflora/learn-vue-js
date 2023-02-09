<template>
  <form v-on:submit.prevent="submitForm">
    <div>
      <label for="username">id: </label>
      <input type="text" id="username" v-model="username">
    </div>
    <div>
      <label for="password">pw: </label>
      <img :src="username" alt="">
      <input type="password" id="password" v-model="password"/>
    </div>
    <button type="submit">Login</button>
  </form>
</template>

<script>
import axios from 'axios';

export default {
  data:function() {
    return {
      username:'',
      password:'123',
    }
  },
  methods:{
    submitForm: function() {
      //event.preventDefault();//form을 제어하는 방식>> v-on:submit.prevent(똑같은 역할을 한다.)
      console.log(this.username, this.password);
      var url = 'https://jsonplaceholder.typicode.com/users';
      var data ={
        username : this.username,
        password: this.password
      }
      axios.post(url, data)//axios는 http통신 라이브러리, fetch(), ajax()  >> post는 데이터를 생성하거나 조작할 때 사용
        .then(function(response){
          console.log(response)
        })
        .catch(function(error){
          console.log(error);
        })
  }  
}
}
</script>

<style>

</style>