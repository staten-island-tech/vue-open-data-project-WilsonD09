<template>
  <router-link :to="airPath" class="card">
    <h2>{{ air.name }}</h2>
    <h3>{{ id }}</h3>
  </router-link>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  pokemon: Object,
  id: Number,
})

const airPath = computed(() => {
  return `/air/${props.id}`
})
</script>

<style scoped></style>
