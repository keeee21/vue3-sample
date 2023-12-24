<script setup lang="ts">
import Card from './Card.vue';
import RocketIconVue from './RocketIcon.vue';

</script>

<template>
  <div class="container">
    <Card title="title" class="card">
      <div class="contents">
        あああ
        <RocketIconVue />
      </div>
    </Card>

    <Card title="aaaa" class="card">
      <div class="contents">
        <RocketIconVue />
        <RocketIconVue />
        <RocketIconVue />
        <RocketIconVue />
      </div>
      <template #footer>
        <div class="footer">
          <span>footer</span>
        </div>
      </template>
    </Card>

    <Card title="vvv" class="card">
      <div class="contents">
        <RocketIconVue />
        Rocket
        <RocketIconVue />
      </div>
    </Card>
  </div>
</template>

<style scoped>
</style>