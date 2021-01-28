<template>
  <div class="hello">
      我是子组件B
      我是子组件B
      我是子组件B
      <div style="margin-top:50px">
      姓：<input type="text" v-model="messsage">
      名：<input type="text" v-model="messagea">
      <p>姓名:{{total}}</p>
      </div>
      <div>
        用户名<input type="text" v-model.lazy="name"><span>{{tip}}</span>
      </div>
  </div>
</template>

<script>
export default {
  name: 'childrenA',
  data () {
    return {
     messsage:'',
     messagea:'',
     name:'',
     tip:'',
    }
  },
  computed: {
    total:function() {
      return this.messsage + this.messagea
    }
  },
  watch: {
    name:function(val) {
      this.checkName(val)
      this.tip = '正在验证中...'
    }
  },
  //写方法函数的
  methods: {
    chidren(id) {
      alert('我是父组件调用时传过来的实参'+id)
    },
    checkName(val){
      let that = this
      //模拟后台接口
      setTimeout(() => {
        if(val == 'admin'){
          this.tip = '用户名不可用'
          return
        }else{
          this.tip = '用户名可以使用'
        }
      },2000)
    }
  },

  
}
</script>


<style scoped>

</style>
