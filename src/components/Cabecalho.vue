
<script setup>
const props = defineProps(['tarefasPendentes']);
</script>

<template>
  <header class="p-5 mb-4 mt-4 bg-light rounded-3">
    <h1 class="text-center">Minhas Tarefas</h1>
    <!-- Exibindo o número de tarefas pendentes -->
    <p class="text-center">Você possui {{ tarefasPendentes.length }} tarefas pendentes</p>
  </header>
</template>

<style scoped>
header {
  background-color: #323538;
  padding: 20px;
  border-radius: 5px;
}
</style>
