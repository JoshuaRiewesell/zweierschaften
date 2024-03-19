<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div class="column">
    <h1>Zweierschaften</h1>
    <form>
      <button class="reset-btton" @click="clearAll()">Reset</button>
    </form>
  </div>
</template>

<script setup lang="ts">
import { usePersonsStore } from '@/stores/persons'

const personsStore = usePersonsStore()

function clearAll() {
  personsStore.removeAllPatients()
}
</script>
