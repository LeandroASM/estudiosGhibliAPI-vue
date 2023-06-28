<template>
  <div id="app">
    <IngresoDatos @hiddenInfo="show=false" @showInfo="show=true"/>
    <Pelis v-if="show"/>
  </div>
</template>

<script>
import IngresoDatos from "@/components/IngresoDatos.vue"
import Pelis from "@/components/MostrarPelis.vue"

export default {
  name: 'App',
  data(){
    return{
      show: false,
    }
  },
  components: {
    IngresoDatos,
    Pelis
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
