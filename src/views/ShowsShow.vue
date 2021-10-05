<template>
  <div class="shows-show">
    <img v-bind:src="show.image" v-bind:alt="show.title" />
    <p>Title: {{ show.title }}</p>
    <p>Year: {{ show.year }}</p>
    <p>Description: {{ show.description }}</p>
    <p>Creator: {{ show.creator }}</p>
    <p>Seasons: {{ show.seasons }}</p>
    <p>Network: {{ show.network }}</p>
    <p>Favorite: {{ show.favorite }}</p>
    <p>User: {{ show.user_id }}</p>
    <router-link v-bind:to="`/shows/${show.id}/edit`">Edit show</router-link>
    <p></p>
    <button v-on:click="destroyShow(show)">Destroy show</button>
    <p></p>
    <router-link to="/shows">Back to all shows</router-link>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      show: {},
    };
  },
  created: function () {
    axios.get("/shows/" + this.$route.params.id).then((response) => {
      console.log("shows show", response);
      this.show = response.data;
    });
  },
  methods: {
    destroyShow: function (show) {
      axios.delete("/shows/" + show.id).then((response) => {
        console.log("shows destroy", response);
        this.$router.push("/shows");
      });
    },
  },
};
</script>
