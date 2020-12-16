<template>
<div style='max-width:300px;background-color:#000000;' >
  <div style="background-color:#000000;height:3px" />
  <div id="app"  style='max-width:290px;background-color:#ffffff;margin:5px;' >
    <li v-for="child in theList" :key="child.msg" id="list" style='list-style-type:none;' >
        <paster :msg=child.msg :cValue=child.cValue :url=child.url />
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
    var rc = await fetch('assets/clipsetdefs.json')
    rc = await rc.json()
    this.theList = rc
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
       theList: this.theList
    }
  },
  mounted()
  {
    this.theList = [ { msg: "TestTitleUrl", cValue: "TestPushUrl", url: "http://www.google.com" },
                       { msg: "TestTitleNon", cValue: "TestPushNon" } ]
    this.getAsset()
  },
  methods:
  {
    getAsset
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
