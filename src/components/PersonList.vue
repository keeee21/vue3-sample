<script setup lang="ts">
import { defineProps, defineEmits } from 'vue'
import { Person } from './Persons.vue'

type Props = {
  persons: Person[];
}

defineProps<Props>();

const emit = defineEmits(['delete-person']);
const deletePerson = (id: number) => {
  if (confirm("Are you sure you want to delete this person?")) {
    emit('delete-person', id);
  }
}

</script>

<template>
  <li v-for="person in persons" :key="person.name" class="person-list">
    <span>{{ person.name }} is {{ person.age }} years old.</span>
    <button @click="deletePerson(person.id)">delete</button>
  </li>
</template>

<style scoped>
.person-list {
  list-style: none;
  margin-bottom: 12px;
  border-radius: 4px;
  font-size: 12px;
  display: flex;
  justify-content: space-between;
  background-color: rgb(204, 219, 233);
  padding: 8px 20px;
  width: 300px;
  align-items: center;
}
</style>