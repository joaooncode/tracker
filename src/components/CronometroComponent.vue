<script setup lang="ts">
import { Play, CircleStop } from 'lucide-vue-next'
import { ref, computed } from 'vue'

defineProps<{
  timerSeconds: number,
  runningTimer: boolean
}>()

const seconds = ref(0)
const isRunningTimer = ref(false)

let timer: number | undefined
const startTimer = () => {
  if (!timer) {
    timer = setInterval(() => {
      seconds.value += 1
    }, 1000)
    isRunningTimer.value = true
  }
}

const stopTimer = () => {
  if (timer && isRunningTimer.value==true) {
    clearInterval(timer)
    timer = undefined
    isRunningTimer.value = false
  }
}

//Calcula o tempo decorrido
const elapsedTime = computed(() => {
  return new Date(seconds.value * 1000).toISOString().substring(11, 19)
})
</script>
<template>
   <span class="text-4xl font-bold">{{ elapsedTime }}</span>
    <button @click="startTimer" :disabled="isRunningTimer==true" class="disabled:bg-gray-300 ml-10 w-30 text-white bg-yellow-900 p-2 rounded-lg hover:bg-yellow-700" title="Iniciar cronômetro">
      <Play color="#fff" :size="40" />
    </button>
    <button @click="stopTimer"  :disabled="isRunningTimer==false" class="disabled:bg-gray-300 ml-10 w-30 text-white bg-yellow-900 p-2 rounded-lg hover:bg-yellow-700" title="Parar cronômetro">
      <CircleStop color="#fff" :size="40" />
    </button>
</template>
