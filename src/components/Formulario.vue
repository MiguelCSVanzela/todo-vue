<script setup>
const props = defineProps(["cadastrarTarefa", "tarefaTemp", "trocarFiltro", "editaTarefaTemp"]); 
</script>

<template>
    <form @submit.prevent="props.cadastrarTarefa">
        <div class="row">
            <div class="col">
                <input :value="props.tarefaTemp" @change="props.editaTarefaTemp" required type="text" class="form-control"
                    placeholder="Digite aqui a descrição da sua tarefa">
            </div>
            <div class="col-md-2">
                <button type="submit" class="btn btn-outline-primary">Cadastrar</button>
            </div>
            <div class="col-md-2">
                <select @change="props.trocarFiltro" class="form-control">
                    <option value="todas">Todas Tarefas</option>
                    <option value="pendentes">Pendentes</option>
                    <option value="realizadas">Realizadas</option>
                </select>
            </div>
        </div>
    </form>
</template>