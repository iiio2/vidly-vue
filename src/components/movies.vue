<template>
  <table class="table table-striped">
    <thead>
      <tr>
        <th>Title</th>
        <th>Genre</th>
        <th>Number In Stock</th>
        <th>Daily Rental Rate</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="movie in movies" :key="movie._id">
        <td>{{ movie.title }}</td>
        <td>{{ movie.genre.name }}</td>
        <td>{{ movie.numberInStock }}</td>
        <td>{{ movie.dailyRentalRate }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { onMounted } from "vue";
import { getMovies } from "../services/fakeMovieService";

const movies = ref(getMovies());

onMounted(() => {
  movies.value;
});
</script>
