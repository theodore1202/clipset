<template>
<div style='max-width:300px;background-color:#000000;' >
  <div style="background-color:#000000;height:3px" />
  <div id="app"  style='max-width:290px;background-color:#ffffff;margin:5px;' >
    <li v-for="child in theList" :key="child.msg" id="list" style='list-style-type:none;' >
        <paster :msg=child.msg :cValue=child.cValue />
       <div style="background-color:#000000;min-height:5px" />
  </li>
  </div>
 
  </div>
</template>

<script>
import Paster from './components/Paster.vue'

async function getAsset()
{
    /* eslint-disable no-unused-vars  */
    var rc = await fetch('../assets/clipsetdef.json')
    rc = await rc.text()
    
    console.log(rc)
}

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
  },
  mounted()
  {
    getAsset()
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

}

</style>
