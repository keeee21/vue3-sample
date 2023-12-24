<script setup lang="ts">
import { ref, defineEmits, computed } from 'vue';

const inputtingName = ref<string>('');
const inputtingAge = ref<number>(0);

const emit = defineEmits(['register-person']);
const register = () => {
  emit('register-person', {
    id : Math.random(),
    name: inputtingName.value,
    age: inputtingAge.value
  });
  inputtingName.value = '';
  inputtingAge.value = 0;
}

const nameLengthLimit = 15;

const isValidName = computed(() => {
  if (inputtingName.value.length >= nameLengthLimit) {
    return false;
  } else {
    return true;
  }
});

const color = computed(() => {
  if (isValidName.value) {
    return 'white';
  } else {
    return 'rgb(244,194,190)';
  }
});

</script>

<template>
  <div class="form-container">
    <div class="input-container">
      <label for="name">name</label>
      <input id="name" name="name" class="input-name" v-model="inputtingName" />
    </div>
    <span v-if="!isValidName">{{ nameLengthLimit }} 文字以内で書いて</span>
    <div class="input-container">
      <label for="age">age</label>
      <input id="age" name="age" type="number" class="input-age" v-model="inputtingAge">
    </div>
    <button :disabled="!isValidName" class="post-button" @click="register()">register</button>
  </div>
</template>

<style scoped>
.form-container {
  flex-direction: column;
  align-items: center;
  background-color: rgb(168, 162, 168);
  padding: 24px;
  width: 400px;
}

.input-name {
  background-color: v-bind(color);
}
</style>