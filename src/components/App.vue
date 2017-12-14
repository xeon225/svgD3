<template>
  <div id="app">
    <div class="mp3">
    
    </div>
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
      var linear = d3.scaleLinear()
                    .domain([0,500])
                    .range([0,100]);

      console.log(linear(50))
      console.log(linear.invert(50))
      console.log(linear.range(50))
    },
    mp3:function(){
      var mp3 = this.d3.select(".mp3").selectAll("a");
      var mp3Data = mp3._groups[0];

      mp3.data(mp3Data)
          // .each(function(d,i){
            // console.log(d.title)
            // mp3.attr("title",'http://tingmp3.520tingshu.com/玄幻奇幻/吞噬星空/'+d.title+'.mp3')
            // .text('http://tingmp3.520tingshu.com/玄幻奇幻/吞噬星空/'+d.title+'.mp3')
          // })
          // .text(function(d,i){
          //   return 'http://tingmp3.520tingshu.com/玄幻奇幻/吞噬星空/'+d.title+'.mp3'
          // })
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
