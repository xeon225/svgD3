<template>
  <div id="app">
    <svg id="ddd"></svg>
    <p>1</p><p>1</p><p>1</p><p>1</p><p>1</p><p>1</p>

  </div>
</template>

<script>
import Lib from 'assets/Lib.js'
export default {
  components: {
  },
  computed:{
    d3:function(){
      return Lib.d3
    }
  },
  methods: {
    ddd:function(){
      var d3 = this.d3;
      var persons = [13,6,9];  
      var p = d3.select("#app").selectAll("p");
      var update = p.data(persons)
      var enter = update.enter()
      var exit =update.exit()

      // var update = p.data(persons).filter(function(d,i){
      //   if(d > 8)
      //   {
      //     console.log(1)
      //     return true;
      //   }
      //   else
      //   {
      //     return false;
      //   }
      // })
      // update.sort(function(a,b){
      //     return b-a;
      // })
      update.text(function(d){return d;})
      enter.append("p")
        .text(function(d){return d;})
      exit.remove()
    }
  },
  ready:function(){
      this.ddd();
      
  }
}
</script>

<style>
html {
  height: 100%;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}

#app {
  color: #2c3e50;
  margin-top: -100px;
  max-width: 600px;
  font-family: Source Sans Pro, Helvetica, sans-serif;
  text-align: center;
}

#app a {
  color: #42b983;
  text-decoration: none;
}

.logo {
  width: 100px;
  height: 100px
}
</style>
