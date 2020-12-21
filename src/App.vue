<template>
  <div id="app">
    <h1 class="rainbow-text">
      PAULOCOACHI - SUA DOSE DE MOTIVAÇÃO E COACH DIÁRIA
    </h1>
    <h2>{{ phrase }}</h2>
    <img class="imgs" alt="Cuchi" src="./assets/cuchi.png" />

    <h1 class="rainbow-text">Caso queira que o cuchi recite, clique aqui</h1>
    <audio controls loop="true">
      <source src="./assets/cuchi.mp3" type="audio/mpeg" codecs="vorbis" />
    </audio>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  data: () => ({
    phrase: "",
  }),
  mounted() {
    this.getPhrase();
  },
  methods: {
    async getPhrase() {
      const data = (await axios.get("https://type.fit/api/quotes")).data;
      this.phrase = data[(data.length * Math.random()) | 0].text;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: cornsilk
}
.imgs {
  width: 100%;
}
.rainbow-text {
  background-image: linear-gradient(
    to left,
    violet,
    indigo,
    blue,
    green,
    yellow,
    orange,
    red
  );
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
</style>
