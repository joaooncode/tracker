<script setup lang="ts">
import { Play, CircleStop } from 'lucide-vue-next'
import { ref, computed } from 'vue'
defineProps<{
  timerSeconds: number
}>()
const seconds = ref(0)
let timer: number | undefined
const startTimer = () => {
  if (!timer) {
    timer = setInterval(() => {
      seconds.value += 1
    }, 1000)
  }
}

const stopTimer = () => {
  if (timer) {
    clearInterval(timer)
    timer = undefined
  }
}

//Calcula o tempo decorrido
const elapsedTime = computed(() => {
  return new Date(seconds.value * 1000).toISOString().substring(11, 19)
})
</script>
<template>
  <div class="container w-full h-20 bg-transparent shadow-lg flex items-center justify-start">
    <input
      type="text"
      placeholder="Qual tarefa você deseja iniciar?"
      class="m-4 px-4 py-2 border-yellow-500 rounded-lg appearance-none focus:border-yellow-500 focus:outline-none w-1/2 border-2"
    />
    <span class="text-4xl font-bold">{{ elapsedTime }}</span>
    <button @click="startTimer" class="ml-10 w-30 text-white bg-yellow-900 p-2 rounded-lg">
      <Play color="#fff" :size="40" />
    </button>
    <button @click="stopTimer" class="ml-10 w-30 text-white bg-yellow-900 p-2 rounded-lg">
      <CircleStop color="#fff" :size="40" />
    </button>
  </div>
</template>
