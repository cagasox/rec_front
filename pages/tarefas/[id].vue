<script setup>
const route = useRoute();
    console.log("route", route);

    const { data: trip } = await useFetch(`http://localhost:8000/tarefasUsuarios?completa`,{
        key:'tripRequest'
    }) 

</script>

<template>
    <div>
        <h1>tarefas detaliadas</h1>
    </div>
</template>