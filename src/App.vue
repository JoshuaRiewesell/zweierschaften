<script setup lang="ts">
import Persons from '@/components/Persons.vue'
import { usePersonsStore } from '@/stores/persons'
import Settings from './components/Settings.vue'

const patientsStore = usePersonsStore()

patientsStore.loadFromLocalStorage()
</script>

<template>
  <main>
    <div class="grid">
      <Settings />
      <Persons />

      <div class="column">
        <h1>Filter</h1>
        <div>
          <button>Gebieten</button>
          <button>Verbieten</button>
        </div>
      </div>

      <div class="column">
        <h1>Sets</h1>
        <form class="sets-form">
          <button type="submit" class="generate-button">Generate</button>
        </form>
        <ul class="set-items"></ul>
      </div>

      <div class="column">
        <h1>Verwendet</h1>
        <div>
          <button>Export</button>
        </div>
        <ul class="usedSet-items"></ul>
      </div>

      <div class="column">
        <h1>Ansicht</h1>
        <div>
          <button onclick="copyView()">Copy</button>
        </div>
        <ul class="pair-items" id="pair-items"></ul>
      </div>
    </div>
  </main>
</template>

<style scoped></style>
