<script setup>
import { reactive } from "vue";
import Cabecalho from "./components/Cabecalho.vue";
import Forms from "./components/forms.vue";
import Tasklist from "./components/tasklist.vue";

const estado = reactive({
  filtro: "todas",
  tarefaTemp: "",
  tarefas: [
    {
      titulo: "Estudar ES6",
      finalizada: false,
    },
    {
      titulo: "Estudar Sass",
      finalizada: false,
    },
    {
      titulo: "Ir para academia",
      finalizada: true,
    },
  ],
});

const getTarefasPendentes = () => {
  return estado.tarefas.filter((tarefa) => !tarefa.finalizada);
};

const getTarefasFinalizadas = () => {
  return estado.tarefas.filter((tarefa) => tarefa.finalizada);
};

const getTarefasFiltradas = () => {
  const { filtro } = estado;

  switch (filtro) {
    case "pendentes":
      return getTarefasPendentes();
    case "finalizadas":
      return getTarefasFinalizadas();
    default:
      return estado.tarefas;
  }
};

const cadastraTarefa = () => {
  const tarefaNova = {
    titulo: estado.tarefaTemp,
    finalizada: false,
  };
  estado.tarefas.push(tarefaNova);
  estado.tarefaTemp = "";
};
</script>

<template>
  <div class="container">
    <!-- Passando as tarefas pendentes para o componente Cabecalho -->
    <Cabecalho :tarefasPendentes="getTarefasPendentes()" />

    <!-- Passando o estado e a função cadastraTarefa para o componente Forms -->
    <Forms :estado="estado" :cadastraTarefa="cadastraTarefa" />

    <!-- Passando as tarefas filtradas para o componente Tasklist -->
    <Tasklist :tarefas="getTarefasFiltradas()" />
  </div>
</template>



