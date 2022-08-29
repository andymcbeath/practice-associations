<script>
import axios from "axios";
export default {
  data: function () {
    return {
      scores: [],
      currentScore: {},
      titleFilter: "",
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
    filterScores: function () {
      return this.scores.filter((score) => {
        var lowerTitle = score.title.toLowerCase();
        var lowerTitleFilter = this.titleFilter.toLowerCase();
        return lowerTitle.includes(lowerTitleFilter);
      });
    },
  },
};
</script>

<template>
  <div class="scores-index">
    <h1>All Scores</h1>
    Search by title:
    <input v-model="titleFilter" list="titles" type="text" />
    <TransitionGroup name="list">
      <datalist id="titles">
        <option v-for="score in scores" v-bind:key="score.id">
          {{ score.title }}
        </option>
      </datalist>
      <div
        v-for="score in filterScores()"
        v-bind:key="score.id"
        v-on:click="currentScore = score"
        v-bind:class="{ selected: score === currentScore }"
      ></div>
    </TransitionGroup>
  </div>
  <div v-for="score in scores" v-bind:key="score.id">
    <h2>{{ score.title }}</h2>
    <p>Composer: {{ score.composer }}</p>
    <p>Score's Flat Id: {{ score.score }}</p>
    <router-link v-bind:to="`/scores/${score.id}`"
      >View and Hear Score</router-link
    >
  </div>
</template>

<style type="text/css">
body {
  margin: 0;
}
#embed-container {
  width: 100%;
  height: 750px;
  margin-top: 40px;
}
</style>
