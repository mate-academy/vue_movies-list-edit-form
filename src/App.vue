<script setup>
import { ref } from 'vue';
import MovieList from './MovieList.vue';
import MovieForm from './MovieForm.vue';

import initialMovies from './data/movies.json';

const movies = ref([...initialMovies]);
const selectedMovie = ref(null);

function onSave(movie) {
  if (selectedMovie.value) {
    Object.assign(selectedMovie.value, movie);
  } else {
    movies.value.push(movie);
  }
}

function onDelete(movie) {
  if (selectedMovie.value?.imdbId === movie.imdbId) {
    selectedMovie.value = null;
  }

  movies.value.splice(movies.value.indexOf(movie), 1);
}
</script>

<template>
  <!-- eslint-disable max-len -->
  <div class="page">
    <div class="page-content">
      <MovieList
        :movies="movies"
        :selected-movie="selectedMovie"
        @select="selectedMovie = $event"
        @delete="onDelete"
      />
    </div>

    <div class="sidebar">
      <MovieForm
        :movie="selectedMovie"
        @save="onSave"
        @cancel="selectedMovie = $event"
      />
    </div>
  </div>
</template>
