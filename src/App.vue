<template>
  <div id="app">
    <wii-first level="1">我是标题 <span style="font-size: 18px;" slot="subtitle">我是subtitle</span></wii-first>
    <wii-second @click.native="nativeClick" @on-click-button="clickButton"></wii-second>
    <wii-third></wii-third>
    <wii-forth></wii-forth>
    <wii-jsx></wii-jsx>
    
    <h3>Functional 函数式组件 ------></h3>
    <input v-model="query" class="functional-input"/>
    <wii-functional>
      <li v-for="(item, index) in computedList"
          :key="item.msg"
          :data-index="index">
          {{item.msg}}
      </li>
    </wii-functional>

    <button @click="changeComponent">点击切换组件</button>
    <wii-choose-comp :component-name="componentName">
      <span>我是{{componentName}}的slot</span>
    </wii-choose-comp>
  </div>
</template>

<script>
import WiiFirst from './components/first/index.vue'
import WiiSecond from './components/second/index.vue'
import WiiThird from './components/third/index.vue'
import WiiForth from './components/forth/index.vue'
import WiiJsx from './components/jsx/index.vue'
import WiiFunctional from './components/functional/index.vue'
import WiiChooseComp from './components/functional/chooseComp.vue'
import WiiCompOne from './components/functional/comp1.vue'
import WiiCompTwo from './components/functional/comp2.vue'

export default {
  name: 'app',
  components: {
    WiiFirst,
    WiiSecond,
    WiiThird,
    WiiForth,
    WiiJsx,
    WiiFunctional,
    WiiChooseComp,
    WiiCompOne,
    WiiCompTwo
  },
  data() {
    return {
      query: '',
      list: [{
        msg: 'Bruce Lee'
      }, {
        msg: 'Jackie Chan'
      }, {
        msg: 'Chuck Norris'
      }, {
        msg: 'Jet Li'
      }, {
        msg: 'Kung Furry'
      }, {
        msg: 'Chain Zhang'
      }, {
        msg: 'Iris Zhao'
      }, ],

      componentName: 'wii-comp-one'
    }
  },
  methods: {
    nativeClick() {
      console.log('这是组件外部click.native触发的事件，第二个组件被点击了')
    },
    clickButton() {
      console.log('这是组件外部触发的【emit】事件，第二个组件被点击了')
    },
    changeComponent() {
      this.componentName = this.componentName == 'wii-comp-one' ? 'wii-comp-two' : 'wii-comp-one'
    }
  },
  computed:{
    computedList: function() {
      var vm = this
      return this.list.filter(function(item) {
        return item.msg.toLowerCase().indexOf(vm.query.toLowerCase()) !== -1
      })
    }
  },
  watch: {
    computedList(newVal, oldVal) {
      console.log(newVal)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;*/
  color: #2c3e50;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

a {
  color: #42b983;
}

.wii-comp-one{
  color: blue;
}
.wii-comp-two{
  color: red;
}

</style>
