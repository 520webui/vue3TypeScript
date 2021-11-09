<template>
  <div class="Gots-wrap">
    <div class="btn" @click="goHome">返回</div>
    <!--挂载DOM元素-->
    <p ref="msg">该节点，有一个ref属性</p>
    <!--挂载子组件-->
    <Child ref="child"/>
    <!--reactive的用法-->
    <div>{{userInfo}}</div>
    <div>{{userInfo.id}}</div>
    <div>{{userInfo.name}}</div>
    <div>{{uidss}}</div>
    <div>{{userLists}}</div>
  </div>
</template>

<script lang="ts">
    import {defineComponent, onMounted,ref, reactive,} from 'vue';
    import {useRouter} from "vue-router";
    import Child from "@components/child.vue";

    interface Member {
      id: number,
      name: string
    };
    export default defineComponent({
        name: "Gots",
        components:{
          Child,
        },
        setup(){
          const msg = ref<HTMLElement | null>(null);
          const child = ref<typeof Child | null>(null);

          const userInfo:Member=reactive({
            id:1,
            name:'zero'
          });
          const uidss:number[]=[1,2,3];
          const userLists:Member[]=reactive([
            {
              id:1,
              name:'zero'
            },
            {
              id:2,
              name:'jjzero'
            },
            {
              id:3,
              name:'QJzero'
            },
          ])
          // 请保证视图渲染完毕后再执行节点操作 e.g. onMounted / nextTick
          onMounted( () => {
            // 比如获取DOM的文本
            console.log(msg.value);

            // 或者操作子组件里的数据
            console.log(child.value);
          });
          const router =useRouter();//路由
          let goHome=()=>{
            router.push({path:'/'});
          }
          return{
            goHome,
            msg,
            child,
            userInfo,
            uidss,
            userLists,
          }
        }
    });
</script>
<style lang="less" scoped>
  .Gots-wrap{
    color: red;
    .btn{
      width: 60px;
      line-height: 40px;
      text-align: center;
      background: tan;
      cursor: pointer;
    }
  }
</style>
