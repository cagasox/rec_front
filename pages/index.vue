<script setup>
    const { data: login } = await useFetch('http://localhost:8000/usuarios')  
</script>

<template>
    <div>
        <h1>Bem Vindo ao Sistema</h1>
        <img src="https://vmxi.com.br/img/login.png" width="200" height="200"> <br>
        <select>
            <option v-for="marea in login.data" 
                :key="marea.id" :value="marea.email">
                {{ marea.email  }}
            </option>  
            </select> <br> <br>
                
                                                
        
    </div>
    <div>
        <NuxtLink to="/Home_page">  
                <button >Fazer Login</button> 
            </NuxtLink>  
    </div>
</template>