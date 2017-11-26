<template>
  <div id="app">
    <svg id="ddd"></svg>
    <p>1111</p>
    <p>2222</p>
    <p>3333</p>
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
            var svg = d3.select("#app").selectAll("p");
            svg.datum(7)
              .append('span')
              .text(function(d,i){
                return d + ' ' + i;
              })
            console.log(svg.datum())
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
