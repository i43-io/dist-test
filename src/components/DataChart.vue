<script setup>
import Highcharts from 'highcharts'
import { ref, watch } from 'vue'

const container = ref(null)

const props = defineProps({ data: { type: Array } })
watch(() => props.data, val => {
  val = val.map(i => [parseFloat(i[0]), i[1]])
  Highcharts.chart(container.value, {
    title: {
      text: ''
    },
    xAxis: {
    },
    series: [{ data: val }]
  })
})
</script>

<template>
<div ref="container" class="chart"></div>
</template>

<style scoped scss>
.chart {
  margin-left: 10px;
  height: 250px;
  width: 640px;
}
</style>