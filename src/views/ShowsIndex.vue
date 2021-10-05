<template>
  <div class="shows-index">
    <h1>All Shows</h1>
    <div v-for="show in shows" v-bind:key="show.id">
      <h2>{{ show.name }}</h2>
      <img v-bind:src="show.url" v-bind:alt="show.name" />
      <p>Title: {{ show.title }}</p>
      <p>Year: {{ show.year }}</p>
      <p>Description: {{ show.description }}</p>
      <p>Creator: {{ show.creator }}</p>
      <p>Seasons: {{ show.seasons }}</p>
      <p>Network: {{ show.network }}</p>
      <p>Favorite: {{ show.favorite }}</p>
      <p>Image: {{ show.image }}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      shows: [],
    };
  },
  created: function () {
    this.indexShows();
  },
  methods: {
    indexShows: function () {
      axios.get("/shows").then((response) => {
        console.log("shows index", response);
        this.shows = response.data;
      });
    },
  },
};
</script>
