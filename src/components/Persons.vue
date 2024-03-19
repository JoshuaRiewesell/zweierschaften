<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div class="column">
    <h1>Personen</h1>
    <form @submit.prevent="addPerson">
      <input
        type="text"
        class="person-input"
        v-model="newPersonName"
        placeholder="Add a person..."
      />
      <button type="submit" class="add-button">Add</button><br />
    </form>
    <!--<input type="file" id="csvFile" accept=".csv" />-->
    <ul>
      <li v-for="(person, index) in persons" :key="index" class="item">
        <input type="checkbox" class="checkbox" />
        {{ person.name }}
        <button class="delete-button" @click="deletePerson(person)">X</button>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { usePersonsStore } from '@/stores/persons'

const store = usePersonsStore()

const persons = store.persons

let newPersonName = ''

const addPerson = () => {
  if (newPersonName.trim() !== '') {
    store.addPerson(newPersonName, false)
    newPersonName = ''
  }
}

const deletePerson = (person: Person) => {
  store.removePerson(person.name)
}
</script>

<style scoped>
.person-input {
  border: none;
  outline: none;
  border-radius: 5px;
  padding: 10px;
  font-size: 1rem;
  width: 100%;
}

form {
  display: flex;
}
</style>
