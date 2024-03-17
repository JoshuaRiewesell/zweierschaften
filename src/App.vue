<script setup lang="ts">
  import Persons from '@/components/Persons.vue'
  import { usePersonsStore } from '@/stores/persons'

  const patientsStore = usePersonsStore()

  patientsStore.loadFromLocalStorage()
</script>

<template>
  <main>
    <Persons />
  </main>
</template>

<style scoped>
</style>