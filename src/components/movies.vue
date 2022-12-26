<template>
  <table class="table table-striped">
    <thead>
      <tr>
        <th>Title</th>
        <th>Genre</th>
        <th>Number In Stock</th>
        <th>Daily Rental Rate</th>
        <th></th>
        <th></th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="movie in movies" :key="movie._id">
        <td>{{ movie.title }}</td>
        <td>{{ movie.genre.name }}</td>
        <td>{{ movie.numberInStock }}</td>
        <td>{{ movie.dailyRentalRate }}</td>
        <td>
          <Like :liked="movie.liked" @click="onLike(movie)" />
        </td>
        <td>
          <button class="btn btn-danger btn-sm" @click="onDelete(movie._id)">
            Delete
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { onMounted } from "vue";
import Movie from "../models/Movie";
import Like from "./common/like.vue";
import { getMovies } from "../services/fakeMovieService";

const movies = ref(getMovies());

onMounted(() => {
  movies.value;
});

const onLike = (movie: Movie) => {
  const index = movies.value.findIndex((m) => m._id === movie._id);
  movies.value[index].liked = !movies.value[index].liked;
};

const onDelete = (id: string) => {
  movies.value = movies.value.filter((movie) => movie._id !== id);
};
</script>
