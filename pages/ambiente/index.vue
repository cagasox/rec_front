<script setup>

    const {data:ambientes}= await useFetch(`http://localhost:8000/ambientes`,{
        key :"sla"
    });
    let nameAmbi;
    const saveAmbiente = async () => {
        await useFetch('http://localhost:8000/ambientes/', {
            method: 'POST', 
            body: [{   
                'nome': nameAmbi 
            }],
            onResponse(){
                refreshNuxtData("sla");
            }
        })
    }
    
</script>
<template>
    <div>
        <h1> ambientes</h1>
    </div>
    <div v-for="ambientesResult in ambientes.data" :key="ambientes.id">
        <h3>ambiente: {{ ambientesResult.nome}}</h3>
  
        <br>
        

    </div>
    <div>
            <h5>cadastre-se novos ambientes</h5>
                    <section>
                        <div>
                            <label for="">nome do ambiente:</label>
                            <input type="text" maxlength="30"  v-model="nameAmbi"/>
                        </div>
                        <br>
                        <br>
                        <div>
                            <button @click="saveAmbiente" > cadastra</button>
                        </div>
                    </section>
                </div>
</template>