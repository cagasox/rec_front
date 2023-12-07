<script setup>
const route = useRoute();
    console.log("route", route);
    
const { data: login } = await useFetch(`http://localhost:8000/usuarios/${route.params.id}` )  
</script>

<template>
    
        <div v-for="usuarios in login.data" :key="usuarios.id">
            <h1>ola {{ usuarios.id }}: {{ usuarios.nome }}</h1>
    </div>
</template>