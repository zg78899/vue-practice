<template>
  <div class="progress"></div>
</template>

<script>
export default {

}
</script>

<style>
.progress{
  background-color:lime;
  height:5px;
  width: 0%;
  /* transition: width 0.7s linear; */
  animation: loading 1s linear ;
}
.complete{
  width:100%;
}
@keyframes loading{
  0% {
    width:0%;
  }
  50%{
    width:50%;
  }
  100%{
    width:100%;
  }
}
</style>