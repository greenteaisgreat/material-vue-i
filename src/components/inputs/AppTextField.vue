<script setup lang="ts">
interface Props {
  label?: string
  modelValue: string
  placeholder?: string
}

const { label, modelValue, placeholder = '' } = defineProps<Props>()

const emit = defineEmits<{
  'update: modelValue': [value: string]
}>()

function handleInput(event: Event) {
  emit('update: modelValue', (event.target as HTMLInputElement).value)
}
</script>

<template>
  <label class="field">
    <span v-if="label">
      {{ label }}
    </span>
    <input :value="modelValue" :placeholder="placeholder" @input="handleInput" />
  </label>
</template>

<style scoped></style>
