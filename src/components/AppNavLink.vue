<script setup lang="ts">
import { computed, ref } from 'vue'

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

// baseline values for Props interface so typescript
// doesn't complain if a value isn't provided
const props = withDefaults(defineProps<Props>(), {
  href: '#',
  dropdown: false,
  items: () => [],
})

// boolean that checks if AppNavLink has been hovered over
const isOpen = ref(false)

// checks for any dropdown items
const hasDropdown = computed(() => props.items.length > 0)

function openMenu() {
  if (hasDropdown.value) {
    isOpen.value = true
  }
}

function closeMenu() {
  isOpen.value = false
}
</script>

<template>
  <div class="nav-link" @mouseenter="openMenu" @mouseleave="closeMenu">
    <a :href="href" class="nav-link__anchor" :aria-expanded="hasDropdown ? isOpen : undefined">
      {{ label }}
      <span v-if="hasDropdown" class="nav-link__caret"> ⏷ </span>
    </a>
    <Transition name="dropdown">
      <div v-if="isOpen" class="nav-link__menu">
        <a v-for="item in items" :key="item.href" :href="item.href" class="nav-link__menu-item">
          {{ item.label }}
        </a>
      </div>
    </Transition>
  </div>
</template>

<style scoped>
.nav-link {
  position: relative;
}

.nav-link__anchor {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  text-decoration: none;
  color: inherit;
  padding: 0.75rem 1rem;
}

.nav-link__caret {
  font-size: 0.75rem;
}

.nav-link__menu {
  position: absolute;
  top: 100%;
  left: 0;
  min-width: 180px;
  background: white;
  border: 1px solid #ddd;
  border-radius: 8px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  z-index: 100;
}

.nav-link__menu-item {
  display: block;
  padding: 0.75rem 1rem;
  text-decoration: none;
  color: inherit;
}

.nav-link__menu-item:hover {
  background: #f5f5f5;
}

/* vue's built-in classes for <Transition />, i.e.,
'enter-active', 'leave-active', etc. */
.dropdown-enter-active,
.dropdown-leave-active {
  transition:
    opacity 0.2s ease,
    transform 0.2s ease;
}

.dropdown-enter-from,
.dropdown-leave-to {
  opacity: 0;
  transform: translateY(-8px);
}
</style>
