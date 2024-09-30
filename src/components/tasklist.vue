
<script setup>
const props = defineProps(['tarefas']);

const toggleTarefaStatus = (tarefa) => {
  tarefa.finalizada = !tarefa.finalizada;
};
</script>

<template>
  <ul>
    <!-- Iterando sobre a lista de tarefas -->
    <li v-for="(tarefa, index) in tarefas" :key="index">
      <!-- Checkbox para marcar/desmarcar como finalizada -->
      <input
        type="checkbox"
        :checked="tarefa.finalizada"
        @change="toggleTarefaStatus(tarefa)"
      />
      <!-- Aplicando a classe done se a tarefa estiver finalizada -->
      <span :class="{ done: tarefa.finalizada }">
        {{ tarefa.titulo }}
      </span>
    </li>
  </ul>
</template>

<style scoped>
ul {
  list-style-type: none;
  padding: 0;
  padding-top: 10px; /* Adicionada a unidade 'px' */
  margin: 0;
}

.done {
  text-decoration: line-through;
}

.task-list li {
  margin-bottom: 15px; /* Ajuste o valor conforme necessário */
}
</style>
