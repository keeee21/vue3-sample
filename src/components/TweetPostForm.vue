<script setup lang="ts">
import { ref, defineEmits } from 'vue';


const inputtingDescription = ref<string>('');

const emit = defineEmits(['post-tweet']);
const postTweet = () => {
  emit('post-tweet', inputtingDescription.value);
  inputtingDescription.value = '';
}
</script>

<template>
  <div class="form-container">
    <input v-model="inputtingDescription" />
    <button class="save-button" @click="postTweet()">post</button>
  </div>
</template>

<style scoped>
input {
  margin-bottom: 16px;
}
.form-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: aliceblue;
  padding: 24px 0;
  width: 600px;
  margin-bottom: 12px;
  border-radius: 4px;
}

.save-button {
  color : #fff;
  font-weight: bold;
  background-color: #68c9c9;
  border-radius: 2px;
}

.save-button:hover {
  cursor: pointer;
  background-color: #37bdbd;
}


</style>