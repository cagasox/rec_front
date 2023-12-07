<script setup>

const {data: alltarefas}=await useFetch('http://localhost:8000/tarefas?all'),{data: tarefasFotos}=await useFetch('http://localhost:8000/fotos');
</script>
<template>
    <div>
        <h1> tarefas</h1>
    </div>
    <div v-for="tarefas in alltarefas.data" :key="tarefas.id">
        <h4>{{ tarefas.nome }}</h4>
        <h4>{{ tarefas.idStatusFK.nome}}</h4>
        <h4>{{ tarefas.prazo}}</h4>
        <h4>{{ tarefas.idAmbienteFK.nome}}</h4>
        <div v-for="(tarefasft,index) in tarefasFotos.id"
        :key="index">
        <img src="http://localhost:8000/fotos" >
        </div>
        <NuxtLink :to="`tarefas/${tarefas.id}`">
            <button>Detailed</button>
        </NuxtLink>
    </div>
</template>
