<template>
  <div class="hello">
    <button v-on:click='onClick()'>{{ msg }}</button>
    <text>{{show}}</text>
  </div>
</template>

<script>

  function onClick()
  {
    console.log(this.cValue)
    console.log(navigator)
    console.log(navigator.clipboard)
    navigator.clipboard.writeText(this.cValue)
    this.errCount=0

    this.pollclip()
  }

function setError()
{
  console.log("SetError")
  this.errCount+=1
  console.log("ErrCount="+this.errCount)
  if(this.errCount===10)
  {
      setDormant()      
  }
  setTimeout(this.pollclip,1000)
}

function doThen(text)
{
    this.errCount = 0;
     if(text!==this.cValue)
    {
      this.setPassive()
      return 
    }
    this.setActive();
    setTimeout(this.pollclip,1000)
}

function pollclip()
{

   /* eslint-disable no-unused-vars  */
  navigator.clipboard.readText().then (text =>  { this.doThen(text) }).catch(rr => { this.setError() })
  
}

function setActive()
{
    console.log("Active")
}
 
 function setDormant()
{
    console.log("Dormant")
}
 
 function setPassive()
{
    console.log("Passive")
}
 

export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    cValue: String
  },
  data()
  {
    return { show: this.show }
  },
  methods:
  {
    onClick: onClick  ,
    pollclip: pollclip,
    setActive,
    setDormant,
    setPassive,
    setError, doThen
  }
 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
