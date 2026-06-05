<script setup lang="ts">
import AppHeader from '@/components/AppHeader.vue'

const links = [
  {
    label: 'Home',
    href: '/',
    id: 1,
  },
  {
    label: 'Products',
    id: 2,
    items: [
      {
        label: 'Buttons',
        href: '/buttons',
        id: 3,
      },
      {
        label: 'Inputs',
        href: '/inputs',
        id: 4,
      },
      {
        label: 'Modals',
        href: '/modals',
        id: 5,
      },
    ],
  },
  {
    label: 'Docs',
    href: '/docs',
    id: 6,
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
