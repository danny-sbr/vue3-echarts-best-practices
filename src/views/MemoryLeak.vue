<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import * as echarts from 'echarts'

const chartDom = ref(null)
let myChart = null

// 圖表配置
const option = {
  xAxis: {
    data: ['小明', '小華', '小美'],
  },
  yAxis: {},
  series: [
    {
      type: 'bar',
      data: [10, 20, 30],
    },
  ],
}

onMounted(() => {
  myChart = echarts.init(chartDom.value)
  myChart.setOption(option)
})

// 在 Vue 3 onUnmount 替 EChart 釋放資源
onUnmounted(() => {
  myChart.dispose()
})
</script>

<template>
  <div ref="chartDom" style="width: 400px; height: 300px"></div>
</template>
