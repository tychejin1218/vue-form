<template>
  <form v-on:submit.prevent="submitForm">
    <div>
      <label for="username">id: </label>
      <input id="username" type="text" v-model="username">      
    </div>
    <div>
      <label for="password">pw: </label>
      <input id="password" type="password" v-model="password">  
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
    submitForm: function(event) {
      // 기본적으로 정의된 이벤트를 실행하지 못하게 하는 메서드 vue에서 v-on:submit.prevent가 동일한 동작을 함
      // event.preventDefault();     
      console.log(this.username, this.password);
      
      var url = "https://jsonplaceholder.typicode.com/users";
      var data = {
        username: this.username,
        password: this.password
      }
      // 터미널에서 npm i axios 명령어로 설치
      // script에서 import axios from 'axios';로 추가
      axios.post(url, data)
       .then(function(response){
         console.log(response);
       })
       .catch(function(error){
         console.log(error);
       });
    }
  }
}
</script>

<style>

</style>