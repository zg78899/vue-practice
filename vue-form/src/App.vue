<template>
  <div id="app">
    <form v-on:submit.prevent="submitForm">
      <div>
        <label for="username">ID: </label>
        <input class="username-input"
        v-bind:class="{'error':isError}" 
        id="username"
         type="text"
          v-model="username">
      </div>
      <div>
        <label for="password">PASSWORD: </label>
        <input id="password" type="password" v-model="password">
      </div>
      <button v-bind:disabled="!isUsernameValid" type="submit">로그인</button>
    </form>
    <!-- v-if="true"이면 보이고 false이면 보이지 않게 된다. -->
    <p v-if="isError">올바르지 않은 아이디 입니다.</p>
    <p v-if="isUsernameValid">올바른 이메일 형식이 입니다.</p>
  </div>
</template>
<script>
//이메일 형식 체크 함수 
function validateEmail(email) {
    const re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
    return re.test(String(email).toLowerCase());
}
export default {
 data(){
   return {
     username:'',
     password:'',
     isError:false
   };
 },
// computed는 데이터가 변화되면 자동으로 불리는 함수 
 computed:{
   //글자를 하나하나 칠때 마다 validation검사, 이메일 조건일 때 isError = true 
   isUsernameValid(){
    return validateEmail(this.username);
   }
 },
 methods:{
   submitForm(){
    //  e.preventDefault();
     console.log('로그인');
    //  axios.post();
    this.isError = true; 
    //  this.initForm();
   },
   initForm(){
     this.username = '';
     this.password = '';
   }
 }
}
</script>
<style scoped>

.username-input{
  outline: none;
}
.username-input.error{
  border:1px solid red;
}


</style>