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
      titulo: "Estudar Estrutura de dados",
      finalizada: false
    },
    {
      titulo: "Estudar Algoritmos",
      finalizada: false
    },
    {
      titulo: "Ir para a Natação",
      finalizada: true
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

