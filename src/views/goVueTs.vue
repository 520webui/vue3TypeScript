<template>
  <div class="goVueTs-wrap">
    <div class="btn" @click="goHome">返回</div>
   <!--vue3的执行生命周期-->
   <!--composition api-->
    <div class="msg">{{msg}}</div>
    <!--ts中的表达方式-->
    <div class="msg">{{msgg}}</div>
    <div class="msg">{{phoneNumber}}</div>
    <!--res API-->
    <div class="msg">{{msgAPI}}</div>
    <div class="msg">{{phoneNumberAPI}}</div>
    <!--ref的简单应该-->
    <!--ref基本类型-->
    <div class="msg">{{msg1}}</div>
    <div class="msg">{{count}}</div>
    <div class="msg">{{isVip}}</div>
    <!--ref引用类型-->
    <div class="msg">{{userInfo}}</div>
    <div class="msg">{{uids}}</div>
    <div class="msg">{{names}}</div>
    <!--ref定义对象树组-->
    <div class="msg">{{memberList}}</div>


  </div>
</template>

<script lang="ts">
    import {defineComponent, ref, reactive,onBeforeMount,onMounted} from 'vue';
    import {useRouter} from "vue-router";
    export default defineComponent({
        name: "goVueTs",
        setup(){
          console.log(111);
          onBeforeMount(()=>{
            console.log(222);
          })
          onMounted(()=>{
            console.log(333);
          })
          console.log(444);
          //执行出的打印顺序 111、444、222、333
          const router =useRouter();//路由
          let goHome=()=>{
            router.push({path:'/'});
          }
          const msg='你好世界 Holly World!';
          const msgg:string='msgg 222';
          const phoneNumber:number| string=13888888888;

          const msgAPI=ref<string>('msgAPI');
          const phoneNumberAPI=ref<string|number>(13888888889);

          //字符串
          const msg1=ref<string>('字符串');
          //数值
          const count=ref<number>(111);
          //布尔值
          const isVip=ref<boolean>(false);
          //声明对象的格式
          interface Member{
            id:number,
            name:string
          };
          //定义一个成员
          const userInfo=ref<Member>({
            id:11,
            name:'JJZERO'
          });
          //定义一个成员组
          const memberList=ref<Member[]>([{
            id:11,
            name:'JJZERO'
          },{
            id:12,
            name:'ZERO'
          }])

          //定义一个普通数组
          const uids=ref<number[]>([1,2,3]);
          //字符串数组
          const names=ref<string[]>(['qin','ji','zero']);

          return{
            goHome,
            msg,
            msgg,
            phoneNumber,
            msgAPI,
            phoneNumberAPI,
            msg1,
            count,
            isVip,
            userInfo,
            memberList,
            uids,
            names,

          }
        }
    });
</script>
<style lang="less" scoped>
  .goVueTs-wrap{
    color: skyblue;
    .btn{
      width: 60px;
      line-height: 40px;
      text-align: center;
      background: tan;
      cursor: pointer;
    }
    .msg{
      color: red;
    }
  }
</style>
