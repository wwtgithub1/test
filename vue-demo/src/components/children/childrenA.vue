<template>
  <div class="hello">
      <p>我是子组件A</p>
      <button @click="son">点击</button>
      <p>我是父组件传过来的{{fatherA}}</p>
  </div>
</template>

<script>
export default {
  name: 'childrenA',
  props: {
    fatherA:{
      // 类型
      type:Object,
      // 默认值
      default:{},
      //是否必须有值传过来
      required:false,
    }
  },
  data () {
    return {
      isIf:true,
    }
  },
  //写方法函数的
  methods: {
    son() {
      this.$emit('ok','我是点击子组件A触发父组件里面的方法')
    }
  },
  //生命周期钩子函数
  beforeCreate() {
    console.log('子组件A初始化前');
  },
  created() {
    console.log('子组件A初始化后');
  },
  beforeMount() {
    console.log('子组件A渲染节点前');
  },
  mounted() {
    console.log('子组件A渲染节点后');
  },

  
}
</script>


<style scoped>

</style>
