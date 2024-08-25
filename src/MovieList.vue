<script setup>
import { defineProps, defineEmits } from 'vue';

const emit = defineEmits(['select', 'delete']);
const { movies, selectedMovie } = defineProps(['movies', 'selectedMovie']);
</script>

<template>
  <TransitionGroup tag="div" class="movies" name="movie-list">
    <div
      class="card"
      :class="{
        'has-background-grey': selectedMovie?.imdbId === movie.imdbId,
      }"
      data-cy="movie"
      v-for="movie of movies"
      :key="movie.imdbId"
    >
      <header class="card-header is-justify-content-space-between">
        <button
          v-if="selectedMovie?.imdbId === movie.imdbId"
          class="card-header-icon"
          data-cy="movie__unselect-button"
          @click="emit('select', null)"
        >
          <span class="icon">
            <i class="fas fa-minus"></i>
          </span>
        </button>

        <button
          v-else
          class="card-header-icon"
          data-cy="movie__select-button"
          @click="emit('select', movie)"
        >
          <span class="icon">
            <i class="fas fa-plus"></i>
          </span>
        </button>

        <button
          class="card-header-icon"
          data-cy="movie__delete-button"
          @click="emit('delete', movie)"
        >
          <span class="icon">
            <i class="fas fa-xmark"></i>
          </span>
        </button>
      </header>

      <div class="card-image">
        <figure class="image is-4by3">
          <img data-cy="movie__image" :src="movie.imgUrl" :alt="movie.title" />
        </figure>
      </div>

      <div class="card-content">
        <div class="media">
          <div class="media-left">
            <figure class="image is-48x48">
              <img src="./assets/images/imdb-logo.jpeg" alt="imdb" />
            </figure>
          </div>

          <div class="media-content">
            <p class="title is-8" data-cy="movie__title">{{ movie.title }}</p>
          </div>
        </div>

        <div class="content">
          <p data-cy="movie__description">{{ movie.description }}</p>
          <a :href="movie.imdbUrl" data-cy="movie__link">IMDB</a>
        </div>
      </div>
    </div>
  </TransitionGroup>
</template>

<style scoped>
.movie-list-enter-active,
.movie-list-leave-active {
  transition: all 0.3s ease;
}
.movie-list-enter-from,
.movie-list-leave-to {
  opacity: 0;
  transform: translateY(-20px);
}
</style>
