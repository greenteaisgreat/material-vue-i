<script setup lang="ts">
import AppHeader from '@/components/AppHeader.vue'

const links = [
  {
    label: 'Home',
    href: '/',
  },
  {
    label: 'Products',
    items: [
      {
        label: 'Buttons',
        href: '/buttons',
      },
      {
        label: 'Inputs',
        href: '/inputs',
      },
      {
        label: 'Modals',
        href: '/modals',
      },
    ],
  },
  {
    label: 'Docs',
    href: '/docs',
  },
]
</script>

<template>
  <AppHeader :links="links" />
</template>

<style>
body {
  background-color: darkslategrey;
}
</style>
