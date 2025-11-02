<template>
    <div class="counter">
        <h2>{{ title }}</h2>
        <p>Count: {{ count }}</p>
        <button @click="increment">Increment</button>
        <button @click="decrement">Decrement</button>
    </div>
</template>

<script setup>
// Accept prop 'initialCount' from parent 'App.vue'
const prop = defineProps({
    initialCount: {
        type: Number,
        default: 0,
    }
})

import { ref } from 'vue'

// Emits 'update' event to parent
const emit = defineEmits(['update'])

// Reactive state for count
const count = ref(prop.initialCount)

function increment() {
    count.value++
    emit('update', count.value)
}

function decrement() {
    if (count.value > 0) {
        count.value--
        emit('update', count.value)
    }
}
</script>

<style>
.counter {
    border: 2px solid #42b983;
    padding: 20px;
    border-radius: 10px;
    width: 200px;
    margin: 20px auto;
    text-align: center;
}

button {
    margin: 5px;
    padding: 10px;
    font-size: 16px;
    cursor: pointer;
}
</style>