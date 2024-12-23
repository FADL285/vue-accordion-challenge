<script setup lang="ts">
import { ref } from 'vue'
import AppAccordion from '@/components/AppAccordion.vue'
import AppAccordionPanel from '@/components/AppAccordionPanel.vue'

const selected = ref([])

const panels = ['Panel 1', 'Panel 2', 'Panel 3', 'Panel 4']
</script>

<template>
  <div>
    <h1>Variant A (single - using v-model)</h1>

    <div class="py-3">
      <div class="form-control" v-for="panel in panels" :key="panel">
        <label class="label cursor-pointer">
          <span class="label-text">{{ panel }}</span>
          <input type="checkbox" class="checkbox" :value="panel" v-model="selected" />
        </label>
      </div>
    </div>

    <div>
      <div class="max-w-xl">
        <AppAccordion multiple v-model="selected">
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
