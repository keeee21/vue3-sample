<script setup lang="ts">
import { defineProps } from 'vue'
defineProps<{
  title: string;
}>();
</script>

<template>
  <div class="card-container">
    <div class="content">
      <span class="title">{{ title }}</span>
      <slot></slot>
    </div>
    <div class="footer">
      <slot name="footer">default footer</slot>
    </div>
  </div>
</template>

<style scoped>
.card-container {
  box-shadow: 2, 8px, black;
  border-radius: 8px;
  padding: 20px;
  width: 300px;
  height: 100px;
  background-color: #ccc;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 15px 0px;
}

.title {
  font-size: 20px;
  font-weight: 600;
}

.footer {
  display: flex;
  height: 30px;
  background-color: rgb(22,119,203);
  width: 100%;
  border-radius: 0px 0px 8px 8px;
  justify-content: center;
  align-items: center;
}
</style>