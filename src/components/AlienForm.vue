<template>
    <div>
         <div class="boton_principal">
        <button type="button" class="btn btn-light" data-bs-toggle="modal" data-bs-target="#exampleModal">
            Crear Nuevo Alien
        </button>
        </div>

        <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
            <div class="modal-dialog">
                <div class="modal-content">
                    <div class="modal-header">
                        <h1 class="modal-title fs-5" id="exampleModalLabel">Crea un Nuevo Alien</h1>
                        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                    </div>
                    <div class="modal-body">
                        <form>
                            <div class="mb-3">
                                <label for="alien-name" class="col-form-label">Nombre:</label>
                                <input type="text" class="form-control" id="alien-name" v-model="newAlien.name">
                            </div>
                            <div class="mb-3">
                                <label for="alien-color" class="col-form-label">Color:</label>
                                <input type="text" class="form-control" id="alien-color" v-model="newAlien.color">
                            </div>
                            <div class="mb-3">
                                <label for="alien-image" class="col-form-label">Imagen:</label>
                                <input type="text" class="form-control" id="alien-image" v-model="newAlien.imagen">
                            </div>
                        </form>
                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cerrar</button>
                        <button type="button" class="btn btn-primary" @click="agregarAlien">Crear Alien</button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Componente hijo que muestra los aliens -->
        <MostrarAliens :aliens="aliens" />
    </div>
</template>

<script>
import MostrarAliens from './MostrarAliens.vue'; 

export default {
    components: {
        MostrarAliens
    },
    data() {
        return {
            aliens: [], // Lista de aliens
            newAlien: {
                name: "",
                color: "",
                imagen: ""
          },
            apikey:"cQEj62AB1vMZ4BPOXi0b2ob9sBy8Dz9M"
      };
        
  },

    methods: {
        agregarAlien() {
            if (this.newAlien.name && this.newAlien.color && this.newAlien.imagen) {
                this.aliens.push({ ...this.newAlien });
                console.log(this.aliens);
                // Reiniciar los campos del formulario
                this.newAlien = {
                    name: "",
                    color: "",
                    imagen: ""
                };
                // Cerrar el modal
                document.getElementById('exampleModal').click();
            } else {
                alert("Por favor complete todos los campos.");
            }
      },
      getgif() {
        fetch("https://api.giphy.com/v1/gifs/random?api_key=${apikey}")
          .then(res => console.log(res))
          .catch(res => console.log(res))
        }
    }
};
</script>

<style>
.boton_principal{
  width: 100%;
  display: flex;
  justify-content: center;
}

.boton_principal .btn{
  margin: 50px;
}
</style>
