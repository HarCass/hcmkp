<script setup lang="ts">
  import { ref } from 'vue';
  import User from './pages/User.vue';

  const count = ref(0);

  function incrementCount (): void {
    count.value++;
  }
</script>

<template>
  <h1>Current Count is: {{ count }}</h1>
  <button @click="incrementCount">Click Me!</button>
  <Suspense>
    <User></User>
  </Suspense>
</template>
