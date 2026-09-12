<script setup>

import { ref } from 'vue';

const id = ref('square')
//const inArea = ref(false)


function mOver() {
    // add code here
    //inArea.value = true;
    id.value = 'circle'
}

function mOut() {
    // add code here
    //inArea.value = false;
    id.value = 'square'
}
</script>

<template>
    <!-- modify code below -->
    <!-- <div :style="{'border-radius': inArea ? '50%' : '0%'}" :id=id @mouseover="mOver" @mouseout="mOut"> -->
    <div :id=id @mouseover="mOver" @mouseout="mOut">
        Mouse Over Me
    </div>

</template>

<style scoped>
#square {
    width: 150px;
    height: 150px;
    background-color: goldenrod;
    text-align: center;
    padding-top: 60px;
}

#circle {
    width: 150px;
    height: 150px;
    border-radius: 50%;
    background-color: goldenrod;
    text-align: center;
    padding-top: 60px;
}
</style>