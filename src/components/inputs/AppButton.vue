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
    <!-- vue's placeholder for the button's label -->
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
  background: oklch(66.375% 0.12558 231.245);
  color: white;
}

.button--secondary {
  background: oklch(50.62% 0.01741 281.596);
  color: white;
}

.button--outlined {
  background: transparent;
  border: 1px solid #ccc;
}

.button--danger {
  background: oklch(58.163% 0.18023 22.146);
  color: white;
}
</style>
