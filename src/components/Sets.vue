<!-- eslint-disable vue/multi-word-component-names -->
<script setup lang="ts">
import { usePersonsStore } from '@/stores/persons'
import { useSetsStore } from '@/stores/sets'

const personsStore = usePersonsStore()
const setsStore = useSetsStore()

function generateSets() {
  setsStore.generateSets(personsStore.persons)
}
</script>

<template>
  <div class="column">
    <h1>Sets</h1>
    <button @click="generateSets()">Generate</button>
    <ul>
      <li v-for="(setOfPairs, index) in setsStore.sets" :key="index" class="item">
        {{ setOfPairs.name }}
        <button class="set-use-button">Use</button>
        <button class="pair-view-button" @click="console.log(setOfPairs)">View</button>
      </li>
    </ul>
  </div>
</template>
