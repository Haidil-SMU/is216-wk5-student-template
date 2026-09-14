<script setup>

import { ref } from 'vue';

const id = ref('circle')
//const inArea = ref(false)


function mOver() {
    // add code here
    id.value = 'square'
}

function mOut() {
    // add code here
    id.value = 'circle'
}
</script>

<template>
    <!-- modify code below -->
    <div :id="id" @mouseover="mOver" @mouseout="mOut">
        Mouse Over Me
    </div>

</template>

<!-- <div :style="{'border-radius': inArea ? '50%' : '0%'}" :id=id @mouseover="mOver" @mouseout="mOut"> -->

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