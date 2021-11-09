<template>
  <div class="home">
    <div @click="goHome">首页</div>
    <div  @click="goTs">ts练习</div>
    <div  @click="goVueTs">vue3+ts练习</div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import {useRouter} from "vue-router";

export default defineComponent({
  name: 'Home',
  components: {

  },
  setup(){
    const router =useRouter();//路由
    let goHome=()=>{
      router.push({path:'/'});
    }
    let goTs=()=>{
      router.push({path:'/goTs'});
    }
    let goVueTs=()=>{
      router.push({path:'/goVueTs'});
    }
    return{
      goHome,
      goTs,
      goVueTs,
    }
  }
});
</script>
<style lang="less" scoped>
  .home{
    color: red;
    font-weight: bolder;
    font-size: 40px;
    display: flex;
    div{
      flex: 1;
      background: tan;
      text-align: center;
      line-height: 80px;
      margin-left: 20px;
      cursor: pointer;
    }
  }
</style>
