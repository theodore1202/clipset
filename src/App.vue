<template>
  <div id="app" >
    <li v-for="child in theList" :key="child.msg" id="list">
        <paster :msg=child.msg :cValue=child.cValue />
  </li>
  </div>
</template>

<script>
import Paster from './components/Paster.vue'

export default {
  name: 'ClipSet',
  components: {
     Paster
  },
  data()
  {
    return {
       theList: [
           { msg: "mantech\\tprevalsky", cValue:"mantech\\tprevalsky"},
           { msg: "tprevalsky", cValue:"tprevalsky"},
           { msg: "mantech:password", cValue:"e5yi7M8T#@"}
       ]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;   
  margin-top: 60px;
}
#list{ align-items: flex-start;}
</style>
