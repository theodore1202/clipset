<template>
  <div class="hello">
    <button v-on:click='onClick()'>{{ msg }}</button>
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

export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    cValue: String
  },
  methods:
  {
    onClick: onClick
  
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
