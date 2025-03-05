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
   <span class="text-4xl font-bold">{{ elapsedTime }}</span>
    <button @click="startTimer" class="ml-10 w-30 text-white bg-yellow-900 p-2 rounded-lg hover:bg-yellow-700" title="Iniciar cronômetro">
      <Play color="#fff" :size="40" />
    </button>
    <button @click="stopTimer" class="ml-10 w-30 text-white bg-yellow-900 p-2 rounded-lg hover:bg-yellow-700" title="Parar cronômetro">
      <CircleStop color="#fff" :size="40" />
    </button>
</template>
