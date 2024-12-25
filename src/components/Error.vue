<script setup>
// 錯誤範例來自於 https://github.com/apache/echarts/issues/13943
import { ref, onMounted, onBeforeUnmount } from 'vue'
import * as echarts from 'echarts'

const chartDom = ref(null)
const chart = ref(null)

const data = ref([
  { value: 820, name: 'A' },
  { value: 932, name: 'B' },
  { value: 901, name: 'C' },
  { value: 934, name: 'D' },
  { value: 1290, name: 'E' },
  { value: 1330, name: 'F' },
  { value: 1320, name: 'G' },
])

const createOption = (data) => {
  return {
    title: {
      text: 'ECharts Example',
    },
    xAxis: {
      type: 'category',
      data: data.map((item) => item.name),
    },
    yAxis: {
      type: 'value',
    },
    series: [
      {
        data: data.map((item) => item.value),
        type: 'line',
      },
    ],
  }
}

const option = createOption(data.value)
console.log(option)

const handleChartResize = () => {
  if (chart.value) {
    chart.value.resize()
  }
}

const resizeChart = () => {
  window.addEventListener('resize', handleChartResize)
}

const initComponent = () => {
  if (chartDom.value) {
    chart.value = echarts.init(chartDom.value)
    chart.value.setOption(option, true)
    resizeChart()
  }
}

onMounted(() => {
  initComponent()
})

onBeforeUnmount(() => {
  window.removeEventListener('resize', handleChartResize)
})
</script>

<template>
  <div ref="chartDom" style="width: 100%; height: 400px"></div>
</template>
