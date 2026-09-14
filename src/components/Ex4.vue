<script setup>
import { ref } from 'vue'
const items = ref(['keyboard', 'mouse', 'iPhone', 'macbook', 'adapter'])
const itemToAdd = ref("")
const text = ref("")

// TODO: Add Code Here

function deleteItem(item) {
    const index = items.value.indexOf(item)
    items.value.splice(index, 1)
}

function addItem() {
    items.value.push(text.value)
    // items.value.push(itemToAdd);
    text.value = ''
}

</script>

<template>

    <h2>Shopping Cart</h2>
    <!-- TODO: Add Code Here -->
    <div>
        <ul>
            <li v-for="item in items">{{item}}
                <button type="button" @click="deleteItem(item)">Delete</button>
            </li>

        </ul>
         <input v-model="text" @keyup.enter="addItem"/>
        <button @click="addItem">Add</button>
        <!-- <input type="text" v-model="itemToAdd">
        <button type="button" @click="addItem(itemToAdd)">Add</button> -->
    </div>

   
</template>
