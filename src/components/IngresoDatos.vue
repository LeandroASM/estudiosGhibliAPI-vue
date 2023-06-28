<template>
  <div>
    <button @click="getInfo">Ingresar Datos</button>

    <div v-if="nombre !=''">
      <h1>Bienvenido {{ fullName }}</h1>
      <p>Aquí podrás encontrar información de películas de anime de estudio Gibli</p>
      <button @click="clearInfo">Limpiar información</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Ingreso-component",
  // props: {},
  data: function () {
    return {
      nombre: "",
      apellido: "",
    };
  },
  computed: {
    fullName() {
      return this.nombre + " " + this.apellido;
    },
  },
  methods: {
    getInfo() {
      this.nombre = prompt("Ingrese nombre");
      this.apellido = prompt("Ingrese Apellido");

      this.$emit("showInfo")
    },
    clearInfo() {
      this.nombre = "";
      this.apellido = "";

      this.$emit("hiddenInfo")
    },
  },
  // watch: {},
  // components: {},
  // mixins: [],
  // filters: {},
  // -- Lifecycle Methods
  // -- End Lifecycle Methods
};
</script>

<style scoped>
</style>