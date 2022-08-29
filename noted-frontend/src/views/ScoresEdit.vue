<script>
import axios from "axios";
import Embed from "flat-embed";

export default {
  data: function () {
    return {
      score: {},
      editScoreParams: {},
      errors: [],
      embed: {},
    };
  },
  created: function () {
    axios.get("/scores/" + this.$route.params.id).then((response) => {
      console.log("scores show", response);
      this.initializeScore(response.data);
      this.editScoreParams = this.score;
    });
  },
  methods: {
    updateScore: function (score) {
      axios
        .patch("/scores/" + score.id, this.editScoreParams)
        .then((response) => {
          console.log("scores update", response);
          this.$router.push("/scores");
        })
        .catch((error) => {
          console.log("scores update error", error.response);
          this.errors = error.response.data.errors;
        });
    },
    initializeScore: function (score) {
      console.log("calling initializeScore");
      const container = document.getElementById("embed-container");
      this.embed = new Embed(container, {
        width: "100%",
        height: "450",
        score: score.score,
        embedParams: {
          mode: "edit",
          appId: "62fa6b1916a2480012017172",
          controlsPosition: "bottom",
        },
      });
    },
  },
};
</script>
// // Export the file when we click on the button // document //
.getElementById("export-xml") // .addEventListener("click", function () { // //
eslint-disable-next-line no-unused-vars // embed.getMusicXML({ compressed: true
}).then(function (_buffer) { // // Exported MusicXML file in `buffer` // }); //
});

<template>
  <div id="embed-container"></div>
  <div class="scores-edit">
    <h1>Update Score Info</h1>
    <form v-on:submit.prevent="updateScore(score)">
      <ul>
        <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
      </ul>
      Title:
      <input type="text" v-model="editScoreParams.title" />
      Composer:
      <input type="text" v-model="editScoreParams.composer" />
      Flat Socre ID #:
      <input type="text" v-model="editScoreParams.score" />
      <input type="submit" value="Update" />
    </form>
  </div>
  <button v-on:click="initializeScore()">Edit Score Info</button>
</template>
