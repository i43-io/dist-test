<script setup>
import { ref } from 'vue'

import DataInput from './components/DataInput.vue'
import DataChart from './components/DataChart.vue'

const data = ref([])
</script>

<template>
  <div class="row">
    <data-input v-model="data" />
    <data-chart :data="data" />
  </div>
</template>

<style scoped>
.row {
  display: flex;
}
</style>
