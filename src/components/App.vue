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
      var persons = [30,20,10,50,40];  
      var min = d3.min(persons, function(d){return d*3});
      var max = d3.max(persons, function(d){return d-5});
      var extent = d3.extent(persons, function(d){return d%7});
      console.log(min);
      console.log(max);
      console.log(extent);
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
