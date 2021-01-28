<template>
  <div class="hello">
    <!-- 更新前后 -->
    <!-- <div v-if="isIf">12315615</div>
    <button @click="trya()">点击</button> -->

    <!-- v-model的使用 -->
      <!-- <div>
      用户名:<input type="text" v-model="form.userName">
      </div>
      <div>
      密码:<input type="password"  v-model="form.password">
      </div>
      <div>
        <label>
            <input type="radio" v-model="form.sel" value="1"> 男
        </label>
        <label>
            <input type="radio" v-model="form.sel" value="2"> 女
        </label>
      </div> -->
      <!-- v-html -->
      <!-- <div v-html="vhtml"></div>
      <div v-text="vtext"></div> -->
      <!-- v-for -->
      <ul>
        <li v-for="item in list" :key="item.id" @click="fun(item.id)">
          {{item.name}}
          <!-- <span v-show="item.id == 1">{{item.name}}</span> -->
          <!-- <span v-if="item.id != 1">{{item.name}}</span>
          <span v-else>我是不显示的</span> -->
        </li>
      </ul>
      <!-- {{form}} -->

      <!-- <div class="stop" @click="fnStop">
        阻止冒泡
        <div>
          <button @click.stop="onStop" style="margin-top: 80px;">点击</button>
        </div>
      </div> -->

    <!-- <childrenA @ok='father' :fatherA='fatherA'></childrenA> -->
    <childrenB ref="childrenB"></childrenB>
  </div>
</template>


<script>
import childrenA from './children/childrenA'
import childrenB from './children/childrenB'

export default {
  name: 'HelloWorld',
  //注册组件
  components: {
    childrenA,
    childrenB,
  },
  data () {
    return {
      // 更新前后
      isIf:true,
      //向子组件传值
      fatherA:{
        id:1,
        name:'王也',
      },
      //v-model
      form:{
        userName:'',
        password:'',
        sel:''
      },
      //v-html
        vhtml:'<p>我是HTML</p>',
      //v-text
        vtext:'<p>我是text</p>',
      //v-for
      list:[
        {id:1,name:'张三',age:18},
        {id:2,name:'李四',age:28},
        {id:3,name:'王五',age:19},
      ]
    }
  },
  //写方法函数的
  methods: {
    trya() {
      this.isIf = !this.isIf
    },

    father(val) {
      console.log(val);
    },
    
    fnStop() {
      alert('我是父元素身上的事件')
    },
    onStop() {
      alert('我是子元素身上的事件')
    },

    fun(id) {
      this.$refs.childrenB.chidren(id)
    }

  },






  //生命周期钩子函数
  beforeCreate() {
    console.log('父组件初始化前');
  },
  created() {
    console.log('父组件初始化后');
  },
  beforeMount() {
    console.log('父组件渲染节点前');
  },
  mounted() {
    console.log('父组件渲染节点后');
  },
  beforeUpdate() {
    console.log('父组件节点更新前');
  },
  updated() {
    console.log('父组件节点更新后');
  },
  beforeDestroy() {
    console.log('父组件组件销毁前');
  },
  destroyed() {
    console.log('父组件组件销毁后');
  },
  
}
</script>


<style scoped>
.stop{
  margin: auto;
  width: 200px;
  height: 150px;
  border: 1px solid #000;
  text-align: center;
  
}
</style>
