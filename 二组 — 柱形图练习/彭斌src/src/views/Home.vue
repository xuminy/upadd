<template>
  <div class="home">
      <div class="HelloWorld echart-box" ref="myechart" id="main">zuo</div> 
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  components: {
  },
   data() {
      return {
        option : {
    color: ['rgb(245,178,108)','rgb(84,187,171)','rgb(163,233,165)' ],
    graphic:{
     type:"text",
     left:"center",
     top:"center",
     style:{
       text:"0\n做题数",
       textAlign:"center",
       fontSize:"30"

     }
    },
    tooltip: {
        trigger: 'item',
        formatter: '{a} <br/>{b}: {c} ({d}%)'
    },
    legend: {
        orient: 'vertical',
        left: 800,
        top:300,
        data: ['考点专练', '套卷练习', '仿真模考']
    },
    series: [
        {
            name: '访问来源',
            type: 'pie',
            radius: ['30%', '60%'],
            avoidLabelOverlap: false,
            label: {
                show: false,
                position: 'inner'
            },
            emphasis: {
                label: {
                    show: true,
                    fontSize: '30',
                    fontWeight: 'bold'
                }
            },
            labelLine: {
                show: false
            },
           
             data: [
                {value: 335, name: '考点专练'},
                {value: 335, name: '套卷练习'},
                {value: 335, name: '仿真模考'},
               
            ],
        }
    ]
}

      }
    },
   
   mounted:function(){
      console.log(this.$echarts)
      let myechart = this.$echarts.init(this.$refs.myechart) //初始化一个echarts
      myechart.setOption(this.option)  //setOption 用this.option中的数据开始作图
    }
}
</script>
<style scoped>
.HelloWorld{  
  width: 1000px;
  height:600px;
  background: white;
  margin: 0 auto;
}
</style>

