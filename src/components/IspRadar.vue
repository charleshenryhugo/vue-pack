<template>
  <div id="IspChart" :style="{width: '1000px', height: '600px'}">
  </div>
</template>

<script>
/* eslint-disable */
let echarts = require('echarts/lib/echarts');
require('echarts/lib/chart/bar');
require('echarts/lib/component/radar');
require('echarts/lib/component/tooltip');
require('echarts/lib/component/title');

// prepare data to be drawn
let groups = ['SUUMO_10', 'SUUMO_20', 'SUUMO_30'];
// average ISPs of each group
let groupISPs = [
  {
    value : [43, 100, 95, 75, 50, 89],
    name : 'ISP_SUUMO_10'
  }, 
  {
    value : [93, 78, 68, 70, 59, 99],
    name : 'ISP_SUUMO_20'
  }, 
  {
    value : [66, 98, 88, 77, 55, 82],
    name : 'ISP_SUUMO_30'
  }
];
// ISP items tested
let ISPItems = [
  {name: 'Sales', max: 100}, {name: 'Administration', max: 100}, 
  {name: 'IT', max: 100}, {name: 'Customer Support', max: 100}, 
  {name: 'Development', max: 100}, {name: 'Marketing', max: 100}
];

export default {
  name: 'IspRadar',
  data () {
    return {
      describe: 'ISP Radar chart based on group average ISP values'
    }
  },
  mounted: function(){
    this.drawRadar();
  },
  methods: {
    drawBar: function(){
        let myChart = echarts.init(document.querySelector('#IspChart'));
        myChart.setOption({
          title: {
              text: 'ECharts 入门示例'
          },
          tooltip: {},
          xAxis: {
              data: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子']
          },
          yAxis: {},
          series: [{
              name: '销量',
              type: 'bar',
              data: [5, 20, 36, 10, 10, 20]
          }]
        });
        this.describe='changed!!';
    },
    drawRadar: function(){
      let myChart = echarts.init(document.querySelector('#IspChart'));
      let option = {
        title: {text: this.describe},
        tooltip: {},
        toolbox: {
          feature: {
            dataView: {show: true, readOnly: true},
            saveAsImage: {show: true}
          }
        },
        legend: {
          data: groups
        },
        radar: {
          name: {
            textStyle: {
              color: '#fff',
              backgroundColor: '#999',
              borderRadius: 3,
              padding: [3, 5]
            }
          },
          indicator: ISPItems
        },
        series: [{
          // name: '预算 vs 开销（Budget vs spending）',
          type: 'radar',
          data: groupISPs
        }]
      }
      myChart.setOption(option, true);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>