<template>
  <div id="particles-js"></div>
</template>
<script>
import particlesData from './particles-data'
export default {
  name:'particles-js',
  props:{
    //   w微粒颜色
      color:{
          type:String,
          default:"#ffffff"
      },
    //   微粒形状
      shapeType:{
          type:String,
          default:'circle'
      },
    //   微粒透明度
      opacity:{
          validator: function(value){
            return value>=0 && value<=1;
          },
          default:0.5
      },
    //   微粒大小
      size:{
          type:Number,
          default:20
      },
      IsLine_linked:{
          type:Boolean,
          default:true
      },
      LineOpacity:{
        validator: function(value){
            return value>=0 && value<=1;
        },
        default:0.9
      },
      LineColor:{
          type:String,
          default:'#ffffff'
      },
      LineWidth:{
          type:Number,
          default:2
      },
      MoveSpeed:{
          type:Number,
          default:10
      },
      hoverEffect: {
        type: Boolean,
        default: false
      },
      hoverMode: {
        type: String,
        default: 'grab'
      },
      clickEffect: {
        type: Boolean,
        default: true
      },
      clickMode: {
        type: String,
        default: 'push'
      },
      particlesJson:{
          type:Object,
          default:null
      }
  },
  mounted(){
      this.init()
  },
  methods:{
      init(){
          require('particles.js')
          if(this.particlesJson!==null){
              particlesJS('particles-js',this.particlesJson)
              return
          }
            particlesJS('particles-js',particlesData({
                color:this.color,
                shapeType:this.shapeType,
                opacity:this.opacity,
                size:this.size,
                IsLine_linked:this.IsLine_linked,
                LineColor:this.LineColor,
                LineOpacity:this.LineOpacity,
                LineWidth:this.LineWidth,
                MoveSpeed:this.MoveSpeed,
                hoverEffect:this.hoverEffect,
                hoverMode:this.hoverMode,
                clickEffect:this.clickEffect,
                clickMode:this.clickMode
            }));
      }
  }
}
</script>
<style scoped>
#particles-js{
    width: 100%;
    height: 100%;
    position: relative;
    top: 0;
    left: 0;
}
</style>
