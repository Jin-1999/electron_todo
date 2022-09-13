<script setup lang="ts">
import * as echarts from 'echarts/core'
import { GridComponent, GridComponentOption } from 'echarts/components'
import { BarSeriesOption, BarChart, LineChart, LineSeriesOption } from 'echarts/charts'
import { UniversalTransition } from 'echarts/features'
import { CanvasRenderer } from 'echarts/renderers'
import { onMounted } from 'vue'

echarts.use([GridComponent, BarChart, LineChart, CanvasRenderer, UniversalTransition])

type EChartsOption = echarts.ComposeOption<GridComponentOption | LineSeriesOption | BarSeriesOption>

onMounted(() => {
  var chartDom = document.getElementById('main')!
  var myChart = echarts.init(chartDom)
  var option: EChartsOption

  option = {
    xAxis: {
      type: 'category',
      data: ['Mach Latte', 'Milk Tea', 'Cheese Cocoa', 'Walnut Brownie']
    },
    yAxis: {},
    series: [
      {
        type: 'bar',
        name: '2015',
        data: [89.3, 92.1, 94.4, 85.4]
      },
      {
        type: 'line',
        name: '2016',
        data: [95.8, 89.4, 91.2, 76.9]
      },
      {
        type: 'line',
        name: '2017',
        data: [97.7, 83.1, 92.5, 78.1]
      }
    ]
  }
  option && myChart.setOption(option)
})
</script>

<template>
  <div id="main"></div>
</template>

<style lang="less">
@import './assets/css/styles.less';
#main {
  width: 800px;
  height: 500px;
  background: #fff;
}
</style>
