<script setup>
const props = defineProps(["tarefas", "tarefasPendentes"]); 
</script>
<template>
    <span v-if="props.tarefasPendentes == 0">Não há tarefas Pendentes a Serem exibidas</span>
    <ul v-else class="list-group mt-4">
        <li class="list-group-item" v-for="tarefa in props.tarefas">
            <input @click="event => tarefa.finalizada = event.target.checked" :checked="tarefa.finalizada"
                :id="tarefa.titulo" type="checkbox">
            <label :class="{ done: tarefa.finalizada === true }" class="ms-3" :for="tarefa.titulo">{{ tarefa.titulo }}
            </label>
        </li>
    </ul>
</template>


<style scoped>
.done {
    text-decoration: line-through;
}
</style>