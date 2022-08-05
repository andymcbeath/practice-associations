<script>
import axios from "axios";
export default {
  data: function () {
    return {
      scores: [],
    };
  },
  created: function () {
    this.indexScores();
  },
  methods: {
    indexScores: function () {
      axios.get("/scores").then((response) => {
        console.log("scores index", response);
        this.scores = response.data;
      });
    },
  },
};
</script>

<template>
  <div class="scores-index">
    <h1>All Scores</h1>
    <div v-for="score in scores" v-bind:key="score.id">
      <h2>{{ score.title }}</h2>
      <img v-bind:src="score.image_file" v-bind:alt="score.title" />
      <p>Composer: {{ score.composer }}</p>
      <p>Image File: {{ score.image_file }}</p>
    </div>
  </div>
</template>
