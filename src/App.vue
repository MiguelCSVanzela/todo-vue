<script setup>

import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';
import ListaDeTarefas from './components/ListaDeTarefas.vue';

const estado = reactive({ 
  filtro: "todas",
  tarefaTemp: '',
  tarefas: [
    {
      titulo: "Estudar Algoritmos",
      finalizada: false
    }
  ]
})

const getTarefasPendentes = () => {
  return estado.tarefas.filter(tarefa => !tarefa.finalizada);
}

const getTarefasFinalizadas = () => {
  return estado.tarefas.filter(tarefa => tarefa.finalizada);
}

const getTarefasFiltradas = () => {
  const { filtro } = estado;

  switch (filtro) {
    case "pendentes":
      return getTarefasPendentes();
    case "realizadas":
      return getTarefasFinalizadas();
    default:
      return estado.tarefas;
  }
}

const cadastrarTarefa = () => {
  const tarefaNova = {
    titulo: estado.tarefaTemp,
    finalizada: false
  }

  estado.tarefas.push(tarefaNova);
  estado.tarefaTemp = "";
}

</script>

<template>
  <div class="container">
    <Cabecalho :tarefas-pendentes="getTarefasPendentes().length" />


    <Formulario :tarefa-temp="estado.tarefaTemp" :edita-tarefa-temp="event => estado.tarefaTemp = event.target.value"
      :cadastrar-tarefa="cadastrarTarefa" :trocar-filtro="event => estado.filtro = event.target.value" />


    <ListaDeTarefas :tarefas="getTarefasFiltradas()" :tarefas-pendentes="getTarefasPendentes().length" />


  </div>
</template>

<style>
  :root{
  --forest: #97D8C4;
  --dark: #2A2D34;
  --rose: #D81159;
  --sky: #118AB2;
  --platium: #E6E8E6;
  --white: #fcfcfc;
  }
  body{
    background-color: var(--platium);
  }

  .container{
    max-width: 1024px;
    width: 100%;
  }
</style>