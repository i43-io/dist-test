<script setup>
import { ref, watch } from 'vue'

import DataInput from './components/DataInput.vue'
import DataChart from './components/DataChart.vue'
import SampleSummary from './components/SampleSummary.vue'

const data = ref([])
const count = ref(300)
const samples = ref([])

function sample(arr, count) {
  const sum = arr.reduce((m, i) => m + i[1], 0)
  let curSum = 0
  let sampled = 0
  return arr.map(([k, v]) => {
    curSum += v
    v = Math.round((curSum / sum) * count - sampled - 1)
    sampled += v
    return [k, v]
  }).filter(i => i[1] > 0)
}

watch(data, val => {
  samples.value = sample(val, count.value)
})
</script>

<template>
  <div class="row">
    <data-input v-model="data" />
    <data-chart :data="data" />
  </div>
  <div class="row">
    <div>
      <input type="number" step="1" placeholder="采样数" v-model="count" />
      <sample-summary :data="data" :samples="samples" />
    </div>
    <data-chart :data="samples" />
  </div>
</template>

<style scoped>
.row {
  display: flex;
}
</style>
