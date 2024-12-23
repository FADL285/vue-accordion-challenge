<script setup lang="ts">
defineProps<{
  title: string
}>()
</script>

<template>
  <div class="bg-base-200 rounded-lg mb-4">
    <div class="p-4 text-xl font-medium">
      {{ title }}
    </div>
    <div class="p-4">
      <slot></slot>
    </div>
  </div>
</template>

<style scoped></style>
