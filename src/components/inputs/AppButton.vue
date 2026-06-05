<script setup lang="ts">
type Variant = 'primary' | 'secondary' | 'outlined' | 'danger'

interface Props {
  variant?: Variant
  disabled?: boolean
}

// baseline values for Props interface so typescript
// doesn't complain if a value isn't provided
const props = withDefaults(defineProps<Props>(), {
  variant: 'primary',
  disabled: false,
})
</script>

<template>
  <button class="button" :class="`button--${props.variant}`" :disabled="props.disabled">
    <slot />
  </button>
</template>

<style scoped>
.button {
  border: none;
  cursor: pointer;
  padding: 0.75rem 1rem;
  border-radius: 8px;
  font-size: 1rem;
}

.button--primary {
  background: #1976d3;
  color: white;
}

.button--secondary {
  background: #666;
  color: white;
}

.button--outlined {
  background: transparent;
  border: 1px solid #ccc;
}

.button--danger {
  background: coral;
  color: white;
}
</style>
