<script setup>
import { ref, onMounted } from 'vue'
import * as echarts from 'echarts'

const chartDom = ref(null)
const chartInstance = ref(null)
const data = ref(null)

const simulatedAPIData = () => {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve([5, 20, 36, 10, 10, 20])
    }, 2000)
  })
}

const fetchData = async () => {
  data.value = await simulatedAPIData()
}

// 圖表選項
const option = {
  title: {
    text: 'ECharts 入門範例',
  },
  tooltip: {},
  xAxis: {
    data: ['襯衫', '羊毛衫', '雪紡衫', '褲子', '高跟鞋', '襪子'],
  },
  yAxis: {},
  series: [
    {
      name: '銷量',
      type: 'bar',
      data: data.value,
    },
  ],
}

// 定義一個函式用於更新數據，模擬用戶操作後的數據變化
const updateData = () => {
  data.value = [15, 25, 40, 20, 15, 30]
}

// 由於 ECharts 需要一個實際存在的 DOM 容器，因此我們必須在元件 Mounted 後才進行初始化
onMounted(() => {
  fetchData()

  if (chartDom.value) {
    chartInstance.value = echarts.init(chartDom.value)
    chartInstance.value.setOption(option)
  }
  watch(
    data,
    (newValue) => {
      option.series[0].data = newValue
      chartInstance.value.setOption(option)
    },
    {
      deep: true,
    },
  )
})
</script>
<template>
  <div>
    {{ data }}
  </div>
  <div class="flex flex-col items-center space-y-4 p-6">
    <div
      ref="chartDom"
      class="h-[400px] w-[600px] rounded-lg border shadow-lg"
    ></div>
    <button
      @click="updateData"
      class="rounded-md bg-blue-500 px-4 py-2 text-white transition-colors duration-200 hover:bg-blue-600 focus:outline-none focus:ring-2 focus:ring-blue-400"
    >
      更新數據
    </button>
  </div>
</template>
