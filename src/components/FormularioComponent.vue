<script setup lang="ts">
  import CronometroComponent from './CronometroComponent.vue'
</script>
<template>
  <div class="container w-full h-20 bg-transparent shadow-lg flex items-center justify-start">
    <input
      type="text"
      placeholder="Qual tarefa você deseja iniciar?"
      class="m-4 px-4 py-2 border-yellow-500 rounded-lg appearance-none focus:border-yellow-500 focus:outline-none w-1/2 border-2"
    />
    <CronometroComponent :timer-seconds="0"/>
  </div>
</template>
