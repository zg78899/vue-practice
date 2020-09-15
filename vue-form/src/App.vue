<template>
  <div id="app">
    <form v-on:submit.prevent="submitForm">
      <div>
        <label for="username">ID: </label>
        <input id="username" type="text" v-model="username">
      </div>
      <div>
        <label for="password">PASSWORD: </label>
        <input id="password" type="password" v-model="password">
      </div>
      <button type="submit">로그인</button>
    </form>
    <!-- v-if="true"이면 보이고 false이면 보이지 않게 된다. -->
    <p v-if="isError">올바르지 않은 아이디 입니다.</p>
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
 computed:{
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

<style>

</style>