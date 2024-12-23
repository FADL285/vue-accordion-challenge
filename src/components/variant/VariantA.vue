<script setup lang="ts">
import { ref } from 'vue'
import AppAccordion from '@/components/AppAccordion.vue'
import AppAccordionPanel from '@/components/AppAccordionPanel.vue'

const selected = ref('')

const panels = ['Panel 1', 'Panel 2', 'Panel 3', 'Panel 4']
</script>

<template>
  <div>
    <h1>Variant A (single - using v-model)</h1>

    <div class="py-3">
      <select class="select select-bordered w-full max-w-xs" v-model="selected">
        <option disabled value="">Please select one</option>
        <option v-for="panel in panels" :key="panel" :value="panel">
          {{ panel }}
        </option>
      </select>
    </div>

    <div>
      <div class="max-w-xl">
        <AppAccordion v-model="selected">
          <AppAccordionPanel v-for="panel in panels" :key="panel" :title="panel">
            <p>{{ panel }} content</p>
            <p>
              Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed non risus. Suspendisse
              lectus tortor, dignissim sit amet, adipiscing nec, ultricies sed, dolor. Cras
              elementum ultrices diam. Maecenas ligula massa, varius a, semper congue, euismod non,
              mi.
            </p>
          </AppAccordionPanel>
        </AppAccordion>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
