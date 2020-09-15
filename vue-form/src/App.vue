<template>
  <div id="app">
    <ProgressBar></ProgressBar>
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
    <p v-if="isSuccess">로그인이 되었습니다.</p>
    <!-- <p v-if="isError">올바르지 않은 아이디 입니다.</p>
    <p v-if="isUsernameValid">올바른 이메일 형식이 입니다.</p> -->
    <!-- isSuceess라는 prop라는 프롭스를 open으로 정의하여 ToastPopup에 내려줌 -->
    <ToastPopup  
    v-bind:open="isSuccess"
     v-on:close="isSuccess = false"
    ></ToastPopup>
  </div>
</template>
<script>
import ToastPopup from '@/components/ToastPopup.vue';
import ProgressBar from '@/components/ProgressBar.vue';
//이메일 형식 체크 함수 
function validateEmail(email) {
    const re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
    return re.test(String(email).toLowerCase());
}
export default {
  components:{
    ToastPopup,
    ProgressBar
    // 'ToastPopup':ToastPopup
  },
 data(){
   return {
     username:'',
     password:'',
     isError:false,
     isSuccess:false
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
    this.isSuccess = true;
    // this.isError = true; 
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
body{
  margin: 0;
}
form {
  padding:5px 10px; 
}
.username-input{
  outline: none;
}
.username-input.error{
  border:1px solid red;
}


</style>