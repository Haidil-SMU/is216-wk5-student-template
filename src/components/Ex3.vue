<script setup>
import { ref, computed } from 'vue'

const x = ref(0)
const y = ref(0)
const lastResult = ref(0)
const operators = ref(["+", "-", "*", "/", "%"])
const selectedOp = ref("+")

// TODO: Add Code Here
// Note: DO NOT USE "eval()". In security, "eval" is considered "evil"!!!
const result = computed(() => {
    if (selectedOp.value == '+') {
        lastResult.value = x.value + y.value;
    }
    else if (selectedOp.value == '-') {
        lastResult.value = x.value - y.value;
    }
    else if (selectedOp.value == '*') {
        lastResult.value = x.value * y.value;
    }
    else if (selectedOp.value == '/') {
        lastResult.value = x.value / y.value;
    } else{
        lastResult.value = x.value % y.value;
    }
    return lastResult
})

    
</script>

<template>
    <p>x <input v-model.number="x"></p> <!-- Whatever the user inputs, store it into the reactive variable x and convert to number-->
    <select v-model="selectedOp"> <!-- Whatever the user chooses, store it into the reactive variable selectedOp-->
        <option v-for="op in operators">{{ op }}</option>
    </select>
    <p>y <input v-model.number="y"></p> <!-- Whatever the user inputs, store it into the reactive variable x and convert to number-->

    <p>---------------------</p>

    <p>= {{ result }}</p>
</template>

<style scoped>
p,
input {
    font-family: monospace;
}

p {
    white-space: pre;
}
</style>
