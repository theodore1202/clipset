<template>
 
    <button v-on:click='onClick()'  
    :class="{ 'GlobalClass': true,
              'Passive': classInUse === 'Passive',
              'Active' : classInUse === 'Active',
              'Dormant' : classInUse === 'Dormant' }"
      >{{ msg }}</button> 
 
</template>

<script>
 
 async function processClick()
 {
     await  navigator.clipboard.writeText(this.cValue)

      this.pollclip()

      if ( this.url != null)
      {
          window.open(this.url,"_blank")
      }
 }

  function onClick()
  {
      this.errCount=0
      this.processClick()
  }

function setError()
{
  console.log("SetError")
  this.errCount+=1
  console.log("ErrCount="+this.errCount)
  if(this.errCount===5)
  {
      this.setDormant()      
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
    this.classInUse = 'Active'
    console.log("Active")
}
 
 function setDormant()
{
   this.classInUse = 'Dormant'
    console.log("Dormant")
}
 
 function setPassive()
{
    this.classInUse = 'Passive'
    console.log("Passive")
}
 

export default {
  name: 'HelloWorld',
  classInUse: 'Passive',

  props: {
    msg: String,
    cValue: String,
    url: String
  },
  data()
  {
    return { show: this.show, classInUse: this.classInUse  }
  },
  methods:
  {
    onClick: onClick  ,
    pollclip: pollclip,
    setActive,
    setDormant,
    setPassive,
    setError, doThen, processClick
  },
 mounted()
  { this.classInUse='Passive'}
 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .Passive
  {
    background-color: #FFFFFF;
    
  }
    .Active
  {
    background-color: #b0b0ff;
  }
  .Dormant
  {
    background-color: #dddddd;
  }
  .GlobalClass
  {
     width: 280px;
     margin-bottom: 3px;
  }
</style>
