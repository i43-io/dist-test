<script setup>
defineProps({
  data: { type: Array },
  samples: { type: Array }
})
</script>

<template>
<pre>
{{ samples.reduce((m, i) => m + i[1], 0) }} / {{ data.reduce((m, i) => m + i[1], 0) }}
{{ samples.map(i => i.join(':')).join('\n') }}
</pre>
</template>

<style scoped lang="scss">
pre {
  max-height: 220px;
  overflow-y: scroll;
}
</style>