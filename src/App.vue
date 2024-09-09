<script setup>
import { reactive } from 'vue';

  const estado = reactive({
    tarefas: [
      {
        titulo: "Estudar Python",
        finalizada: false,
      },
      {
        titulo: "Arrumar a cama",
        finalizada: false,
      },
      {
        titulo: "Jogar AC Rogue",
        finalizada: true,
      },
    ]
  })

  const getTarefasPendentes = () => {
    return estado.tarefas.filter(tarefa => !tarefa.finalizada)
  }
</script>

<template>
<div class="container">
  <header class="p-5 mb-4 mt-4 bg-light rounded-3">
    <h1>Minhas Tarefas</h1>
    <p>
      Voce possue {{ getTarefasPendentes().length }} tarefas pendentes
    </p>
  </header>
  <form action="">
    <div class="row">
      <div class="col">
        <input type="text" placeholder="Digite aqui a descrição da tarefa" class="form_control">
      </div>
      <div class="col-md-2">
        <button type="submit" class="btn btn-primary">Cadastrar</button>
      </div>
      <div class="col-md-2">
        <select class="form-control">
          <option value="todas">Todas Taferas</option>
          <option value="pendentes">Pendentes</option>
          <option value="finalizadas">Finalizadas</option>
        </select>
      </div>
    </div>
  </form>
  <ul class="list-group mt-4">
    <li class="list-group-item" v-for="tarefa in estado.tarefas">
      <input :checked="tarefa.finalizada" :id="tarefa.titulo" type="checkbox">
      <label :class="{done: tarefa.finalizada}" class="ms-3" :for="tarefa.titulo">
        {{tarefa.titulo}}
      </label>
    </li>
  </ul>
</div>
</template>

<style scoped>
  .done {
    text-decoration: line-through;
  }
</style>
