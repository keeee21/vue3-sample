<script setup lang="ts">
import { Ref, ref } from 'vue';
import PersonList from './PersonList.vue';
import PersonPostForm from './PersonPostForm.vue';

export type Person = {
  id: number;
  name: string;
  age: number;
}

const persons: Ref<Person[]> = ref([
  {
    id: 0,
    name: 'John',
    age: 20
  },
  {
    id: 1,
    name: 'Jane',
    age: 21
  },
]);

const register = ( person: Person ) => {
  persons.value.push(person);
}

const deletePerson = (id: number) => {
  persons.value = persons.value.filter((person: Person) => person.id !== id);
}
</script>

<template>
  <div class="container">
    <h1>Persons</h1>
    <PersonPostForm @register-person="register" />

    <div class="persons-container">
      <p v-if="persons.length <= 0">No persons have been added</p>
      <ul>
        <PersonList :persons="persons" @delete-person="deletePerson"/>
      </ul>
    </div>
  </div>
</template>

<style scoped>

.input-container {
  align-items: center;
  margin: 5px;
  display: flex;
  justify-content: space-evenly;
}

.post-button {
  margin-top: 24px;
  color : #fff;
  font-weight: bold;
  background-color: #68c9c9;
  border-radius: 2px;
}
</style>