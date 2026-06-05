<script setup lang="ts">
import AppNavLink from './AppNavLink.vue'

interface NavItem {
  label: string
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
      <AppNavLink
        v-for="link in links"
        :key="link.label"
        :label="link.label"
        :href="link.href"
        :dropdown="link.dropdown"
        :items="link.items"
      />
    </nav>
  </header>
</template>

<style scoped></style>
