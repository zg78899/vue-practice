<template>
  <div class="toast" 
  v-bind:class="{'animation':open}">
     로그인 완료 되었습니다.
  </div>
</template>
<script>
let timer;
export default {
  props:['open'],
  watch:{
    //open이라는 프롭스의 값이 바뀔대 마다 watch가 적용됨
    //newValue 새로운 값이 들어올때 마다
    open(newValue){
      if(newValue){
        console.log('토스트 팝업열기');
        clearTimeout(timer)
        timer = setTimeout(()=>{
         this.$emit('close');
        },2000)
      }
    }
  }
}
</script>
<style scoped>
.toast{
  width:200px;
  height:40px;
  background-color:rgba(0, 0, 0, 0.5);
  color:#fff;
  display:flex;
  justify-content: center;
  align-items:center;
  position: fixed;
  bottom: -5%;
  left: 5%;
  transition: bottom 0.5s linear;

}
.animation{
  bottom: 5%;
  background-color:black;
}
</style>