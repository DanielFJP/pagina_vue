<template>
<div class="contador">    
<h1>Contador</h1>
<h2>{{ contador }}</h2>
<div class="botones">
<button type="button" class="btn btn-success" @click="incrementar">+1</button>
<button type="button" class="btn btn-danger" @click="decrementar">-1</button>
</div>
</div>
</template>

<script setup >

import { ref } from 'vue';

        const contador = ref(0);

        const incrementar = () => {
            contador.value++;
        };

        const decrementar = () => {
            contador.value--;
        };

</script>

<style scoped>

.contador{
    width: 100%;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 100px;
    color: white;
}

.botones{
    flex-direction: row;
}

.botones button{
    width: 80px;
    margin: 20px;
}
</style>