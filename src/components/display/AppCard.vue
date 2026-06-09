<script setup lang="ts">
interface Props {
  elevated?: boolean
}

const props = withDefaults(defineProps<Props>(), {
  elevated: true,
})
</script>

<template>
  <section class="card" :class="{ 'card--elevated': props.elevated }">
    <slot />
  </section>
</template>

<style scoped>
.card {
  padding: 1rem;
  border-radius: 12px;
  border: 1px solid #ddd;
}

.card--elevated {
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.8);
}
</style>
