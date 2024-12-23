<script setup lang="ts">
import { inject, ref, readonly, computed } from 'vue'
import { injectionKey } from './AppAccordion.vue'

const props = defineProps<{
  title: string
}>()

const accordionProvider = inject(injectionKey, {
  withinAccordion: false,
  registerPanel: () => {},
  activePanels: readonly(ref<string | string[]>()),
  togglePanel: () => {},
  multiple: false,
})

if (!accordionProvider.withinAccordion) {
  throw new Error('AppAccordionPanel must be used within an AppAccordion')
}

const isActive = computed(() => {
  // if multiple, check if the activePanels array includes the title
  if (accordionProvider.multiple) {
    return Array.isArray(accordionProvider.activePanels.value)
      ? accordionProvider.activePanels.value.includes(props.title)
      : false
  }

  return accordionProvider.activePanels.value === props.title
})
</script>

<template>
  <div class="bg-base-200 rounded-lg mb-4">
    <div
      class="p-4 text-xl font-medium cursor-pointer"
      @click="accordionProvider.togglePanel(title)"
    >
      {{ title }}
    </div>
    <div class="p-4" v-if="isActive">
      <slot></slot>
    </div>
  </div>
</template>

<style scoped></style>
