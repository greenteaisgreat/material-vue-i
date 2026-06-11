<script setup lang="ts">
import NavLink from '@/components/navigation/NavLink.vue'

interface NavItem {
  label: string
  id: string | number
  href?: string
  dropdown?: boolean
  items?: {
    label: string
    href: string
  }[]
}

defineProps<{
  links: NavItem[]
}>()
</script>

<template>
  <header class="header">
    <nav class="header__nav">
      <NavLink
        v-for="link in links"
        :key="link.id"
        :label="link.label"
        :href="link.href"
        :dropdown="link.dropdown"
        :items="link.items"
      />
    </nav>
  </header>
</template>

<style scoped>
.header {
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  padding: 0 2rem;
  border-bottom: 1px solid #ddd;
  height: 64px;
}

.header__nav {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
}
</style>
