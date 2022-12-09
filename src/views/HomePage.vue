<script setup>
import MovieCard from "../components/MovieCard.vue";
import { ref } from "vue";

const popularMovies = ref(null);
const popularSeries = ref(null);

try {
  const moviesRes = await fetch(
    "https://api.themoviedb.org/3/movie/popular?api_key=f3764e9b52bcedab6431af751cd6106a&language=en-US&page=1"
  );
  const { results: moviesResults } = await moviesRes.json();
  popularMovies.value = moviesResults;

  const seriesRes = await fetch(
    "https://api.themoviedb.org/3/tv/popular?api_key=f3764e9b52bcedab6431af751cd6106a&language=en-US&page=1"
  );
  const { results: seriesResults } = await seriesRes.json();
  popularSeries.value = seriesResults;
} catch (e) {
  console.log(e);
}

function handleListScroll({ target }) {
  const { scrollLeft, nextElementSibling } = target;
  if (scrollLeft >= 10) {
    nextElementSibling.classList.add("opacity-0");
  } else {
    nextElementSibling.classList.remove("opacity-0");
  }
}
</script>

<template>
  <main>
    <section id="poupular-movies">
      <div class="mx-auto max-w-7xl px-4 pt-8">
        <h1 class="text-xl font-bold">Popular Movies</h1>
        <div class="relative">
          <div
            @scroll="handleListScroll"
            class="mt-8 flex gap-4 overflow-x-auto pb-12"
          >
            <MovieCard
              v-for="movie in popularMovies"
              :key="movie.id"
              :title="movie.title"
              :vote_average="movie.vote_average"
              :poster_path="movie.poster_path"
            />
          </div>
          <div
            class="pointer-events-none absolute top-0 right-0 h-[calc(100%-2rem)] w-[20%] bg-gradient-to-r from-transparent to-white transition"
          ></div>
        </div>
      </div>
    </section>
    <section id="popular-series">
      <div class="mx-auto max-w-7xl px-4 py-8">
        <h1 class="text-xl font-bold">Popular Series</h1>
        <div class="relative">
          <div
            @scroll="handleListScroll"
            class="mt-8 flex gap-4 overflow-x-auto pb-12"
          >
            <MovieCard
              v-for="movie in popularSeries"
              :key="movie.id"
              :title="movie.name"
              :vote_average="movie.vote_average"
              :poster_path="movie.poster_path"
            />
          </div>
          <div
            class="pointer-events-none absolute top-0 right-0 h-[calc(100%-2rem)] w-[20%] bg-gradient-to-r from-transparent to-white transition"
          ></div>
        </div>
      </div>
    </section>
  </main>
</template>

<style></style>
