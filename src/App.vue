<script setup lang="ts">
import AppHeader from '@/components/layout/AppHeader.vue'
import AppButton from './components/inputs/AppButton.vue'
import AppCard from './components/display/AppCard.vue'
import AppTextField from './components/inputs/AppTextField.vue'

import { ref } from 'vue'

const email = ref('')
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
  <AppButton variant="secondary"> Test </AppButton>
  <AppCard>
    <h2>Profile</h2>
    <p>User Information</p>
  </AppCard>
  <AppTextField v-model="email" label="Email" />
</template>

<style>
body {
  background-color: darkslategrey;
}
</style>
