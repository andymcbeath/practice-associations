<script>
import axios from "axios";
import Embed from "flat-embed";

export default {
  data: function () {
    return {
      score: {},
      embed: {},
    };
  },
  created: function () {
    axios.get("/scores/" + this.$route.params.id).then((response) => {
      console.log("scores show", response);
      this.initializeScore(response.data);
      this.score = response.data;
    });
  },
  methods: {
    destroyScore: function (score) {
      axios.delete("/scores/" + score.id).then((response) => {
        console.log("scores destroy", response);
        this.$router.push("/scores");
      });
    },
    // eslint-disable-next-line no-unused-vars
    initializeScore: function (score) {
      const container = document.getElementById("embed-container");
      this.embed = new Embed(container, {
        width: "100%",
        height: "450",
        score: score.score,
        embedParams: {
          appId: "62fa6b1916a2480012017172",
          controlsPosition: "bottom",
        },
      });
    },
  },
};
</script>

<template>
  <div class="scores-show">
    <h2>{{ score.title }}</h2>
    <p>Composer: {{ score.composer }}</p>
    <p>Score's Flat ID: {{ score.score }}</p>
    <router-link v-bind:to="`/scores/${score.id}/edit`">Edit Score</router-link>
    <button v-on:click="destroyScore(score)">Destroy Score</button>
    <router-link to="/scores">Back to All Scores</router-link>
  </div>
  <div id="embed-container"></div>
</template>
