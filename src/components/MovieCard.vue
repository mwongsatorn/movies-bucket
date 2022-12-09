<script setup>
defineProps({
  title: {
    type: String,
    default: "Title",
  },
  vote_average: {
    type: Number,
    default: 0,
  },
  poster_path: {
    type: String,
    default: null,
  },
});
</script>

<template>
  <div
    class="relative flex w-[250px] shrink-0 flex-col overflow-hidden rounded-xl shadow-lg"
  >
    <img
      v-if="poster_url !== null"
      :src="`https://image.tmdb.org/t/p/w500/${poster_path}`"
      alt=""
    />
    <img v-else src="https://placehold.co/250x375?text=No+Poster" alt="" />
    <div
      class="absolute bottom-0 right-0 h-[50%] w-full bg-gradient-to-b from-transparent to-black"
    ></div>
    <div
      title="something"
      class="absolute bottom-2 w-full truncate whitespace-nowrap px-4 font-bold text-white"
    >
      {{ title }}
    </div>
    <div
      class="absolute top-2 left-2 flex h-8 w-8 items-center justify-center rounded-full bg-red-700 font-bold text-white"
    >
      {{ vote_average }}
    </div>
  </div>
</template>
