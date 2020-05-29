<template>
  <div class="hello">
    <div id="lxy_id">
    </div>
  </div>
</template>

<script>
var echarts = require('echarts');
export default {
  name: 'HelloWorld',
  data () {
    return {
      list:['考点专练', '套卷练习', '仿真模考'],
      arr:[
        {value: 335, name: '考点专练'},
        {value: 310, name: '套卷练习'},
        {value: 234, name: '仿真模考'}
       ],
       col:["#f5b26c","#54bbab","#a3e9a5"]
    }
  },
  mounted() {
    this.back()
  },
  methods: {
    back(){
      //获取节点
      var myChart = echarts.init(document.getElementById('lxy_id'));  
      //给该节点绑定echarts
      myChart.setOption({
          title:{
            text:"标题",//可以添加标题
            left: 400,//修改距离
          },
          tooltip: {
              trigger: 'item',//气泡提示配置，可以修改为axis
              formatter: '{a} <br/>{b}: {c} ({d}%)'
          },
          legend: { //图例配置
              orient: 'vertical',
              top:"center",
              right: 10, //legend各个item的间隔
              data: this.list //图例显示的数据
          },
          toolbox:{ //工具箱，可以对数据进行批量修改
              show:true,
              feature:{
                mark:{  //相关标记
                  show:true 
                },
                dataView:{  //修改标记
                  show:true,
                  readOnly:false //判断数据是否可以刷新，true则不能修改
                },
                magicType:{ //是否进行类型切换
                  show:true,
                  type:["line","bar"]
                },
                restore:{ //是否进行刷新
                  show:true 
                },
                savaAsImage:{ //是否保存图片
                  show:true
                },
              }
          },
          calaulable:true,  //实现拖拽混合计算的功能
          series: [
              {
                  name: '访问来源',
                  type: 'pie',
                  radius: ['30%', '70%'],
                  avoidLabelOverlap: false,
                  label: {
                      show: false,
                      position: 'center',
                  },
                  emphasis: {
                      label: {
                          show: true,
                          fontSize: '20',
                          fontWeight: 'bold'
                      }
                  },
                  labelLine: {
                      show: false
                  },
                  data: this.arr,//数据设置
                  color:this.col,//颜色设置
                  xAxis:[
                    //直角X坐标系设置
                  ],
                  yAxis:[
                    //直角Y坐标系设置
                  ]
              }
          ]
      });
    }

  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#lxy_id{
  width: 600px;
  height: 300px;
  margin-top: 100px;
}
</style>
