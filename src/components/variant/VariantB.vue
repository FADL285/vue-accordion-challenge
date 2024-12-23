<script setup lang="ts">
import AppAccordion from '@/components/AppAccordion.vue'
import AppAccordionPanel from '@/components/AppAccordionPanel.vue'

const panels = ['Panel 1', 'Panel 2', 'Panel 3', 'Panel 4']
</script>

<template>
  <div>
    <h1 class="py-3">Variant A (single - without v-model)</h1>

    <div>
      <div class="max-w-xl">
        <AppAccordion>
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
