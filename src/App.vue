<template>
  <div v-if="info" class="card">
    <header class="header">{{ info.title }}</header>
    <div class="description" v-html="info.description"></div>
  </div>
</template>

<script>
import axios from "axios";

let cursoMostrado = 1;

export default {
  name: "App",
  data() {
    return {
      info: null,
    };
  },

  created() {
    axios
      .get("https://www.alura.com.br/api/formacoes")
      .then((response) => (this.info = response.data[cursoMostrado]));
  },
};
</script>

<style>
.card {
  border: 1px solid;
  display: flex;
  flex-direction: column;
  font-family: Roboto, sans-serif;
}
header {
  background-color: blueviolet;
  text-align: center;
  color: #fff;
  font-size: 1.8rem;
  height: 15vh;
  display: flex;
  justify-content: space-around;
  align-items: center;
}

.description ul li {
  list-style: none;
}
</style>
