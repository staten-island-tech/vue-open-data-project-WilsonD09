<template>
  <div class="card">
    <h1>{{ air.spc_common }}</h1>
    <h2>{{ air.status }}</h2>
    <h3>{{ id + 1 }}</h3>
  </div>
</template>

<script setup>
const props = defineProps({
  air: Object,
  id: Number,
})
</script>

<style scoped></style>
