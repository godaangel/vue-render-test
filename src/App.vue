<template>
  <div id="app">
    <wii-first level="1">我是标题 <span slot="subtitle">subtitle</span></wii-first>
  </div>
</template>

<script>
import WiiFirst from './components/first/index.vue'
export default {
  name: 'app',
  components: {
    WiiFirst
  },
  data () {
    return {
      
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
