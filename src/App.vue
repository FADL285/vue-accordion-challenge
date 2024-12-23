<script setup lang="ts">
import { ref, defineAsyncComponent } from 'vue'

const variants = ['A', 'B', 'C', 'D', 'E']
const selectedVariant = ref('A')

const components = variants.map((variant) => {
  return defineAsyncComponent(() => import(`@/components/variant/Variant${variant}.vue`))
})
</script>

<template>
  <main class="container px-6 mx-auto">
    <div>
      <!-- Variant Buttons -->
      <div class="py-6 flex justify-center space-x-4">
        <button
          v-for="variant in variants"
          :key="variant"
          @click="selectedVariant = variant"
          :class="[selectedVariant === variant ? 'btn-primary' : 'btn-neutral', 'btn']"
        >
          Variant {{ variant }}
        </button>
      </div>

      <div>
        <component :is="components[variants.indexOf(selectedVariant)]" />
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}
</style>
