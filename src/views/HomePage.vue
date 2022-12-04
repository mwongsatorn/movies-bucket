<script setup>
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
          ></div>
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
          ></div>
          <div
            class="pointer-events-none absolute top-0 right-0 h-[calc(100%-2rem)] w-[20%] bg-gradient-to-r from-transparent to-white transition"
          ></div>
        </div>
      </div>
    </section>
  </main>
</template>

<style></style>
