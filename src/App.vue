<template>
  <h1>Vue Counter App</h1>

  <!-- Prop to pass into Counter + event binding -->
  <Counter :initialCount="1" @update="handleUpdate" />
</template>


<script setup>
import { ref } from 'vue'
import Counter from './components/Counter.vue'

const parentCount = ref(1)

function handleUpdate(newCount) {
  parentCount.value = newCount
  console.log('Count updated to: ', parentCount.value)
}
</script>