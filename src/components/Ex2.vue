<script setup>
import { ref } from 'vue'

const teamA = ref('Falcons')
const teamB = ref('Tigers')
const scoreA = ref(0)
const scoreB = ref(0)
const step = ref(1) // points added per click
const maxScore = ref(10)

function addA() {
  // add points to Team A, maximum is 10
  scoreA.value = Math.min(maxScore.value, scoreA.value + step.value)
}

function addB() {
  // add points to Team B, maximum is 10
  scoreB.value = Math.min(maxScore.value, scoreB.value + step.value)
}

function reset() {
  // reset both scores
  scoreA.value = 0
  scoreB.value = 0
}
</script>

<template>
  <div style="font-family: Arial; max-width: 520px; margin: 24px auto">
    <h2>Mini Scoreboard</h2>

    <p>
      <strong>{{ teamA }}</strong> vs <strong>{{ teamB }}</strong>
    </p>

    <p>Current: {{ scoreA }} - {{ scoreB }}</p>

    <!-- B. In-template expressions go here -->
    <p>Total points: {{ scoreA + scoreB }}</p>
    <p>Points left to win: {{ maxScore - Math.max(scoreA, scoreB) }}</p>

    <!-- A. Event handlers go here -->
    <div style="display: flex; gap: 12px; margin: 12px 0">
      <button @click="addA">+ Team A</button>
      <button @click="addB">+ Team B</button>
      <button @click="reset">Reset</button>
    </div>

    <div style="margin-top: 14px">
      <!-- C. Display winner / status here -->
      <div v-if="scoreA === maxScore">
        Winner: {{ teamA.toUpperCase() }}
      </div>

      <div v-else-if="scoreB === maxScore">
        Winner: {{ teamB.toUpperCase() }}
      </div>

      <div v-else>
        No winner yet. Keep playing!
      </div>
    </div>
  </div>
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