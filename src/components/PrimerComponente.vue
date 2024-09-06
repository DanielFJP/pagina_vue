<template>
    <div class="imagen">
        <img :src="image" :alt="text">
    </div>
</template>

<script>
export default {
    name: 'PrimerComponente',
    data() {
        return {
            image: require("../assets/nave.png"),
            text: "Nave espacial"
        }
    }
}
</script>

<style>
  .imagen{
    width: 100%;
    height: auto;
    margin-top: 30px;
    display: flex;
    justify-content: center;
  }

  .imagen img{
    width: 20% ;
    height: 20%;
  }
</style>