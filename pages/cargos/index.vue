<script setup>

const {data:cargos}= await useFetch(`http://localhost:8000/cargos`,{
        key :"sla"
    });
    let namecargo;
    const savecargo = async () => {
        await useFetch('http://localhost:8000/cargos`', {
            method: 'POST', 
            body: [{   
                'nome': namecargo,
                'nivelAcesso': nivelAcess
            }],
            onResponse(){
                refreshNuxtData("sla");
            }
        })
    }
  
</script>
<template>
    <div>
        <h1>CARGOS</h1>
    </div>
    <div v-for="cargosResult in cargos.data" :key="cargos.id">
        <h3>cargo: {{ cargosResult.nome}}</h3>
        <h3>nivel de acesso: {{ cargosResult.nivelAcesso }}</h3>
  
        <br>

    </div>
    <div>
            <h5>cadastre-se novos ambientes</h5>
                    <section>
                        <div>
                            <label for="">nome do cargo:</label>
                            <input type="text" maxlength="30"  v-model="namecargo"/>
                        </div>
                        <br>
                        <div>
                            <label for="">nivel de acesso:</label>
                            <input type="text" maxlength="30"  v-model="nivelAcess"/>
                        </div>
                        <br>
                        <div>
                            <button @click="savecargo" > cadastra</button>
                        </div>
                    </section>
                </div>
</template>