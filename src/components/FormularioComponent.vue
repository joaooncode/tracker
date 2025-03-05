<script setup lang="ts">
  import CronometroComponent from './CronometroComponent.vue'
  import { ref } from 'vue';

  const taskDescription = ref('')

const finishTask = (elapsedTime: number) : void => {
  console.log('Tempo da tarefa: ' + elapsedTime);
  console.log('Descrição da tarefa: ' + taskDescription.value);
  taskDescription.value = ''
}


</script>
<template>
  <div class="container w-full h-20 bg-transparent shadow-lg flex items-center justify-start">
    <input
    v-model="taskDescription"
      type="text"
      placeholder="Qual tarefa você deseja iniciar?"
      class="m-4 px-4 py-2 border-yellow-500 rounded-lg appearance-none focus:border-yellow-500 focus:outline-none w-1/2 border-2"
    />
    <CronometroComponent :runningTimer="false" :timer-seconds="0" @timer-finished="finishTask"/>
  </div>
</template>
