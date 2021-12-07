<template>
  <div class="meteo">
    <div class="container">
      <h1 class="my-4">App Meteo Vue.js</h1>
      <div class="form-group mb-5">
        <label for="position">Entrez le nom d'une ville</label>
        <input
          type="text"
          id="position"
          class="form-control"
          v-model="requete"
          @keypress.enter="goMeteo"
        />
      </div>
      <div class="w-75 m-auto" v-if="temps">
        <h3 class="text-center">Postion: {{ temps.name }}</h3>
        <div class="card text-center p-5">
          <p class="text-affichage">Temperature : {{ temps.main.temp }}°</p>
          <p class="text-affichage">
            Temps: {{ temps.weather[0].description }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Meteo",
  data() {
    return {
      requete: "",
      temps: undefined,
      api_code: "baae11bea4be685204c42c7772aeb568",
      url_search: "https://api.openweathermap.org/data/2.5/weather?",
    };
  },
  methods: {
    goMeteo() {
      axios
        .get(
          `${this.url_search}q=${this.requete}&units=metric&appid=${this.api_code}&lang=fr`
        )
        .then((response) => {
          this.temps = response.data;
          console.log(this.temps);
        });
      this.requete = "";
    },
  },
};
</script>

<style scoped>
</style>
