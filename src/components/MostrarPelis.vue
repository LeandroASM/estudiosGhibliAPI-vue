<template>
  <div>
    <div>
      <p>A continuación hay un listado con los nombres de las películas</p>
    </div>
    <div>
      <select @change="getPeli" v-model="filmSelect">
        <option value="" selected>Seleccione película</option>
        <option v-for="film in films" :key="film.name" :value="film.name">
          {{ film.name }}
        </option>
      </select>
      <div class="row justify-content-center mt-5 mb-4">
        <div v-if="film" class="card p-0" style="width: 18rem">
          <img :src="film.poster" class="card-img-top img-fluid" alt="film.name" />
          <div class="card-body">
            <h3 class="card-title">
              <strong>Título original:</strong> {{ film.hepburn }}
            </h3>
            <h6 class="card-title">
              <strong>Título en Inglés:</strong> {{ film.title }}
            </h6>
            <p class="card-text">
              <strong>Descripción:</strong>{{ film.synopsis }}
            </p>
          </div>
          <ul class="list-group list-group-flush">
            <li class="list-group-item"><strong>Director: </strong>{{ film.director }}</li>
            <li class="list-group-item"><strong>Duración: </strong>{{ film.runtimeMinutes }}</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "pelis-component",
  // props: {},
  data: function () {
    return {
      films: [],
      filmSelect: "",
      film: null,
    };
  },
  // computed: {},
  methods: {
    getFilms() {
      axios
        .get("https://studio-ghibli-films-api.herokuapp.com/api/")
        .then((json) => {
          console.log(json);

          for (const key in json.data) {
            let film = {
              name: key,
              data: json.data[key],
            };
            this.films.push(film);
          }
        })
        .catch((err) => console.log(err));
    },
    getPeli() {
      if (this.filmSelect != "") {
        let Peli = this.films.find((film) => film.name === this.filmSelect);
        this.film = Peli.data;
      }
    },
  },
  // watch: {},
  // components: {},
  // mixins: [],
  // filters: {},
  // -- Lifecycle Methods
  created() {
    this.getFilms();
  },
  // -- End Lifecycle Methods
};
</script>

<style scoped>
</style>