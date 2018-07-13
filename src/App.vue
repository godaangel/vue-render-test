<template>
  <div id="app">
    <wii-first level="1">我是标题 <span style="font-size: 18px;" slot="subtitle">我是subtitle</span></wii-first>
    <wii-second @click.native="nativeClick" @on-click-button="clickButton"></wii-second>
    <wii-third></wii-third>
  </div>
</template>

<script>
import WiiFirst from './components/first/index.vue'
import WiiSecond from './components/second/index.vue'
import WiiThird from './components/third/index.vue'
export default {
  name: 'app',
  components: {
    WiiFirst,
    WiiSecond,
    WiiThird
  },
  data () {
    return {
      
    }
  },
  methods: {
    nativeClick() {
      console.log('这是组件外部触发的事件，第二个组件被点击了')
    },
    clickButton() {
      console.log('这是组件外部触发的【emit】事件，第二个组件被点击了')
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

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
