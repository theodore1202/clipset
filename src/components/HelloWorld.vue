<template>
  <div class="hello">
    <button v-on:click='onClick()'>{{ show }}</button>
  </div>
</template>

<script>

  function onClick()
  {
    console.log(this.cValue)
    console.log(navigator)
    console.log(navigator.clipboard)
    navigator.clipboard.writeText(this.cValue)
  }


function pollclip()
{
  var self = this
  
   /* eslint-disable no-unused-vars  */
    navigator.clipboard.readText().then (text =>  { self.show = text }).catch(err => {})

  setTimeout(self.pollclip,5)
}

function mounted()
{
  this.show = this.msg;
  this.pollclip();
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
    pollclip: pollclip
  },
  mounted: mounted
 
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
