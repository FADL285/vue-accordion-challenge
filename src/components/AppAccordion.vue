<script setup lang="ts">
import { ref, provide, readonly } from 'vue'

const props = defineProps<{
  multiple: boolean
}>()

const panels = ref<string[]>([])

const activePanels = defineModel<string | string[]>()

function registerPanel(title: string) {
  // check if the panel is already registered
  if (panels.value.includes(title)) {
    console.warn(`Panel with title "${title}" is already registered`)
    return
  }

  panels.value.push(title)
}

// check if the panel is already active should be toggled, if not, add it to the activePanels
function togglePanel(title: string) {
  if (props.multiple) {
    // check if activePanels is undefined or empty
    if (!activePanels.value || activePanels.value.length === 0) {
      activePanels.value = [title]
      return
    }

    // check if the panel is already active
    if (activePanels.value.includes(title)) {
      if (Array.isArray(activePanels.value)) {
        activePanels.value = activePanels.value.filter((panel) => panel !== title)
      }
    } else {
      activePanels.value = [...activePanels.value, title]
    }
  } else {
    activePanels.value = title
  }
}

provide(injectionKey, {
  withinAccordion: true,
  registerPanel,
  activePanels: readonly(activePanels),
  togglePanel,
  multiple: props.multiple,
})
</script>
<script lang="ts">
import type { InjectionKey, Ref } from 'vue'
export const injectionKey = Symbol('AppAccordion') as InjectionKey<{
  withinAccordion: boolean
  registerPanel: (title: string) => void
  activePanels: Readonly<Ref<string | readonly string[] | undefined>>
  togglePanel: (title: string) => void
  multiple: boolean
}>
</script>

<template>
  <div>
    <slot></slot>
  </div>
</template>

<style scoped></style>
