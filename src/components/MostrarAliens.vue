<template>
    <div class="container MostrarAliens">
        <div class="alien-text">
            <h1 v-if="!selectAlien">Seleccione un Alienigena.</h1>
        </div>
        <div v-if="selectAlien" class="alien-img">
            <img :src="selectAlien.imagen" :alt="selectAlien.name"/>
            <p>Este es el alien {{ selectAlien.name }} y es de color {{ selectAlien.color }}.</p>
        </div>
    

    <div class="Boton_Alien">
       <button type="button" class="btn btn-warning" 
       v-for="alien in aliens"
       :key="alien.name"
       @click="seleccion(alien)">

       {{ alien.name }}

       </button>
    </div>
</div>
</template>

<script>
export default {

    props: {
        aliens: Array
    },
    
    data() {
        return {
            selectAlien: null  
        };
    },

    methods: {
        seleccion(alien) {
            this.selectAlien = alien;
        }
    }
};
</script>

<style scoped>
.container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    text-align: center;
    height: 50vh;
}

.alien-text h1 {
    font-size: 35px;
    margin-bottom: 80px;
    color: #ffffff;
    font-family: monospace;
}

.alien-img img {
    max-width: 250px;
    margin-bottom: 20px;
    border-radius: 20px;
}

.alien-img p {
    font-size: 20px;
    color: #ffffff;
    font-family: monospace;
}

.Boton_Alien{
    display: flex;
    justify-content: center;
    gap: 30px
}

.Boton_Alien .btn{
    padding: 10px 20px;
    font-size: 16px;
}
</style>


