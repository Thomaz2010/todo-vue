<script setup>
const props = defineProps(['estado', 'cadastraTarefa']);
</script>

<template>
  <form @submit.prevent="cadastraTarefa">
    <div class="row">
      <div class="col">
        <input
          :value="estado.tarefaTemp"
          required
          @input="(evento) => (estado.tarefaTemp = evento.target.value)"
          type="text"
          placeholder="Digite a descrição da Tarefa"
          class="form-control"
        />
      </div>
      <div class="col-md-1">
        <button type="submit" class="btn btn-primary">Cadastrar</button>
      </div>
      <div class="col-md-2">
        <select
          @change="(evento) => (estado.filtro = evento.target.value)"
          class="form-control"
        >
          <option value="todas">Todas Tarefas</option>
          <option value="pendentes">Pendentes</option>
          <option value="finalizadas">Finalizadas</option>
        </select>
      </div>
    </div>
  </form>
</template>
