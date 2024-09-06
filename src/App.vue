<template>
  <div id="app">
    <TablaPersonas/>
    <!--<ContContador />
    <PrimerComponente />
    <AlienForm />
    <AlienBotones/>-->
    
  </div>
</template>

<script>
import TablaPersonas from './components/TablaPersonas.vue';
/*import PrimerComponente from './components/PrimerComponente.vue';
import AlienBotones from './components/MostrarAliens.vue';
import AlienForm from './components/AlienForm.vue';
import ContContador from './components/ContContador.vue';*/

export default {
  name: 'App',
  components: {
    TablaPersonas
    /*PrimerComponente,
    AlienBotones,
    AlienForm
    ContContador*/
  },
}
</script>

<style>
#app {
  background-color: rgb(0, 0, 0);
}

html, body {
  margin: 0;
  padding: 0;
  background-color: rgb(0, 0, 0);
}
</style>
