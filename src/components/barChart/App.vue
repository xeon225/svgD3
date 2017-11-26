<template>
  <div id="app">
    
  </div>
  <span @click="mysort()" v-text="'排序'"></span>
  <span @click="myadd()" v-text="'增加数据'"></span>
</template>

<script>
import Lib from 'assets/Lib.js'
export default {
  data () {
    return {
      dataset : [50,43,120,87,99,167,142],
      svg:'',
      width : 400,
      height : 400,
      padding : {top:20, right:20, bottom:20, left:20},
      rectStep : 35,
      rectWidth : 30
    }
  },
  components: {
  },
  computed:{
    d3:function(){
      return Lib.d3
    }
  },
  methods: {
    ddd:function(data){
      var d3 = this.d3;
      var dataset = data;
      var width = this.width;
      var height = this.height;
      this.svg = d3.select("#app")
        .append("svg")
        .attr("width",width)
        .attr("height",height);

      

      this.darw(dataset,this.svg);
    },
    darw:function(data,svg){
      var dataset = data;
      var height = this.height;
      var padding = this.padding;
      var rectStep = this.rectStep;
      var rectWidth = this.rectWidth;
      var updateRect = svg.selectAll("rect")
                      .data(dataset);
      var enterRect = updateRect.enter();
      var exitRect = updateRect.exit();

      this.updateRect(updateRect,enterRect,exitRect,height,padding,rectStep,rectWidth);

      var updateText = svg.selectAll("text")
                      .data(dataset);
      var enterText = updateText.enter();
      var exitText = updateText.exit();

      this.updateText(updateText,enterText,exitText,height,padding,rectStep,rectWidth);
    },
    updateRect:function(update,enter,exit,height,padding,rectStep,rectWidth){
      update.attr("fill","steelblue")
                  .attr("x",function(d,i){
                    return padding.left + i * rectStep;
                  })
                  .attr("y",function(d){
                    return height - padding.bottom - d
                  })
                  .attr("width",rectWidth)
                  .attr("height",function(d){
                    return d
                  });
      enter.append("rect")
                  .attr("fill","steelblue")
                  .attr("x",function(d,i){
                    return padding.left + i * rectStep;
                  })
                  .attr("y",function(d){
                    return height - padding.bottom - d
                  })
                  .attr("width",rectWidth)
                  .attr("height",function(d){
                    return d
                  });
      exit.remove();
    },
    updateText:function(update,enter,exit,height,padding,rectStep,rectWidth){
      update.attr("fill","white")
                  .attr("font-size","14px")
                  .attr("text-anchor","middle")
                  .attr("x",function(d,i){
                    return padding.left + i * rectStep;
                  })
                  .attr("y",function(d){
                    return height - padding.bottom - d
                  })
                  .attr("dx",rectWidth/2)
                  .attr("dy","1em")
                  .text(function(d){
                    return d;
                  })
      enter.append("text")
                  .attr("font-size","14px")
                  .attr("text-anchor","middle")
                  .attr("fill","white")
                  .attr("x",function(d,i){
                    return padding.left + i * rectStep;
                  })
                  .attr("y",function(d){
                    return height - padding.bottom - d
                  })
                  .attr("dx",rectWidth/2)
                  .attr("dy","1em")
                  .text(function(d){
                    return d;
                  })
      exit.remove();
    },
    mysort:function(){
      var d3 = this.d3;
      var data = this.dataset.sort(d3.ascending);
      var svg = this.svg;
      this.darw(data,svg);
    },
    myadd:function(){
      var d3 = this.d3;
      this.dataset.push(Math.floor(Math.random() * 100));
      var data = this.dataset;
      var svg = this.svg;
      this.darw(data,svg);
    }
  },
  ready:function(){
      this.ddd(this.dataset);
      
  }
}
</script>

<style>


</style>
