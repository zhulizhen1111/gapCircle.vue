<template>
     <div class="repair-order">
       <div class="tt-echarts">
        <div id="detail_bill" style=" width: 200px;height: 200px;"> </div>
        <div class="tt-legend">
          <div><div class="square"></div>运行类工单<span class="num">500</span><span class="rat">40%</span></div>
          <div><div class="square" style="border:1px solid #6ECAF7"></div>巡检类工单<span class="num">400</span><span class="rat">38%</span></div>
          <div><div class="square" style="border:1px solid #73DA99"></div>维保类工单<span class="num">100</span><span class="rat">30%</span></div>
          <div><div class="square" style="border:1px solid #F3E171"></div>维修类工单<span class="num">100</span><span class="rat">22%</span></div>
          <div><div class="square" style="border:1px solid #FABA53"></div>综合类工单<span class="num">100</span><span class="rat">18%</span></div>
        </div>
      </div>
     </div>
  </div>
</template>

<script>
import axios from 'axios';
var echarts = require("echarts")
export default {
  components: {

  },

  mixins: [],
  props: {
     
  },

  data () {
    return {
     
        
    }
  },

  computed: {

  },
 
  mounted() {
    this.$nextTick(function(){
      this.draw()
    })
    
  },
 

  methods: {
      
      draw() {
          let myChart = echarts.init(document.getElementById('detail_bill'));

          var scaleData = [{
                  'name': '运行类工单',
                  'value': 500
              },
              {
                  'name': '巡检类工单',
                  'value': 400
              },
              {
                  'name': '维保类工单',
                  'value': 100
              },
              {
                  'name': '维修类工单',
                  'value': 100
              },
              {
                  'name': '综合工单',
                  'value': 100
              },
          ];

          var placeHolderStyle = {
              normal: {
                  label: {
                      show: false
                  },
                  labelLine: {
                      show: false
                  },
                  color: 'rgba(0, 0, 0, 0)',
                  borderColor: 'rgba(0, 0, 0, 0)',
                  borderWidth: 0
              }
          };
          var data = [];

          var color = ['#73DA99', '#FABA53', "#4A9EF9",'#6ECAF7','#F3E171']
          for (var i = 0; i < scaleData.length; i++) {
              data.push({
                  value: scaleData[i].value,
                  name: scaleData[i].name,
                  itemStyle: {
                      normal: {
                          borderWidth: 15,
                          borderColor: color[i],
                      }
                  }
              }, {
                  value: 5,
                  name: '',
                  itemStyle: placeHolderStyle
              });
          }

          var seriesObj = [{
              name: '',
              type: 'pie',
              clockWise: false,
              radius: [50, 50],
              hoverAnimation: false,
              itemStyle: {
                  normal: {
                      label: {
                          show: true,
                          position: 'center',
                          color: '#3B4254',
                          fontSize:0,
                          formatter: function(params) {                   
                              return '\n\n\n\n\n\n\n'
                          },
                      },

                  }
              },
              data: data
          }];

          myChart.setOption({
            tooltip: {
                show: false
            },
            legend: {
                show: false
            },
            toolbox: {
                show: true
            },
            series: seriesObj
          });

        }
  },

}
</script>

<style scoped lang="less" >
.online-people-detail {
    position: fixed;
    z-index: 999;
    top: 50px;
    right: 0;
    bottom: 0;
    background: #FFFFFF;
    box-shadow: 0 7px 15px 0 rgba(0,0,0,0.20);
    transition: all 0.5s ease-in-out;
     .tt-echarts{
       display: flex;
        #detail_bill{
          margin-top: 30px;
          
        }
      .tt-legend{
        margin-top: 61px;
        >div{
          height: 30px;
        }
        .square{
          width: 8px;
          height: 8px;
          background: #fff;
          border: 1px solid #4A9EF9;
          border-radius: 50px;
          display: inline-block;
          margin-right: 10px;
        }
        .num{
          margin-left: 15px;
        }
        .rat{
          margin-left: 15px;
        }
      }
     }
     }
   
   
}
</style>
