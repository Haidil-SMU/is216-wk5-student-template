<script setup>
import { ref } from 'vue'
const items = ref(['keyboard', 'mouse', 'iPhone', 'macbook', 'adapter'])
const itemToAdd = ref("")

// TODO: Add Code Here

function deleteItem(item) {
    const index = items.value.indexOf(item)
    items.value.splice(index, 1)
}

function addItem(itemToAdd) {
    items.value.push(itemToAdd);
    console.log(items);
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
        <input type="text" v-model="itemToAdd">
        <button type="button" @click="addItem(itemToAdd)">Add</button>
    </div>

   
</template>
