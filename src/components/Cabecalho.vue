<script setup>
const props = defineProps(["tarefasPendentes"])
</script>

<template>
    <header class="p-5 my-4 header text-center" >
        <h1 class="text-uppercase display-5">Minhas Tarefas</h1>
        <p>Você possui <span>{{ props.tarefasPendentes }}</span> tarefas pendentes</p>
    </header>
</template>

<style scoped>
.header {
    background-color: var(--dark); 
    color: var(--platium); 
    border-radius: 8px;
}

span{
    color: var(--sky)
}
</style>