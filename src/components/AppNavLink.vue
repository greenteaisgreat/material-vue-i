<script setup lang='ts'>
import {computed, ref} from 'vue'

interface DropdownItem {
  label: string
  href: string
}

interface Props {
  label: string
  href?: string
  dropdown?: boolean
  items?: DropdownItem[]
}

const props = withDefaults(defineProps<Props>(), {
  href: '#',
  dropdown: false,
  items: () => []
})

// boolean that checks if AppNavLink has been hovered over
const isOpen = ref(false)

// checks for any dropdown items
const hasDropdown = computed(
  () => props.dropdown && props.items.length > 0
)

function openMenu() {
  if (hasDropdown.value) {
    isOpen.value = true;
  }
}

function closeMenu() {
  isOpen.value = false
}
</script>

<template>
  <div
    class='nav-link'
    @mouseenter='openMenu'
    @mouseleave='closeMenu'
  >
  </div>
</template>

<style scoped>

</style>
