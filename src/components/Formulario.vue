<script setup>
const props = defineProps(["cadastrarTarefa", "tarefaTemp", "trocarFiltro", "editaTarefaTemp"]); 
</script>

<template>
    <form @submit.prevent="props.cadastrarTarefa">
        <div class="row">
            <div class="col">
                <input :value="props.tarefaTemp" @change="props.editaTarefaTemp" required type="text" class="form-control task-input"
                    placeholder="Digite aqui a descrição da sua tarefa">
            </div>
            <div class="col-md-2">
                <button type="submit" class="btn text-uppercase">Cadastrar</button>
            </div>
            <div class="col-md-2">
                <select @change="props.trocarFiltro" class="form-control task-state">
                    <option value="todas">Tarefas</option>
                    <option value="pendentes">Pendentes</option>
                    <option value="realizadas">Realizadas</option>
                </select>
            </div>
        </div>
    </form>
</template>

<style scoped>
.task-input {
    background-color: var(--dark);
    transition: all 0.5s ease-in;
    
    &::placeholder{
        color: var(--platium); 
    }
    
    &:focus{
       border: 1px solid var(--sky);
       box-shadow: none;
   }
}

.task-state{
    text-transform: uppercase;
    text-align: center;
    transition: all 0.2s ease-in;
    
    &:focus{
        box-shadow: none;
    }

    &:hover{
        background-color: var(--sky);
        color: var(--platium); 
        cursor: pointer;
    }

}
.btn{
    color: var(--dark); 
    border-color: var(--dark);
        
    &:hover {
        background-color: var(--dark); 
        color: var(--platium); 
    }
}
</style>