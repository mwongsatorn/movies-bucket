<script setup>
import IconSearch from "./Icons/IconSearch.vue";
import IconCross from "./Icons/IconCross.vue";
import { ref, onMounted, onUnmounted } from "vue";

const emit = defineEmits(["expandSearchbar", "closeSearchbar"]);
const isSearchbarExpanded = ref(false);

function expandSearchbar() {
  isSearchbarExpanded.value = true;
  emit("expandSearchbar");
}

function closeSearchbar() {
  isSearchbarExpanded.value = false;
  emit("closeSearchbar");
}

onMounted(() => {
  window.addEventListener("resize", handleResize);
});

onUnmounted(() => {
  window.removeEventListener("resize", handleResize);
});

function handleResize() {
  if (window.innerWidth >= 640) {
    isSearchbarExpanded.value = false;
    emit("closeSearchbar");
  }
}
</script>

<template>
  <button
    @click="closeSearchbar"
    :class="[isSearchbarExpanded ? '' : 'hidden']"
    class="rounded-full px-1.5 py-1.5 hover:bg-red-700 hover:text-white sm:hidden"
  >
    <IconCross class="h-6 w-6"></IconCross>
  </button>
  <div class="w-full" :class="[isSearchbarExpanded ? '' : 'hidden sm:block']">
    <div class="flex">
      <input
        class="w-full rounded-l-xl border-2 px-4 py-1 focus:border-black focus:outline-none"
        type="text"
        placeholder="Search for a movie, serie or a person..."
      />
      <button class="rounded-r-xl bg-red-700 px-4 text-white">
        <IconSearch class="h-6 w-6"></IconSearch>
      </button>
    </div>
  </div>
  <button
    @click="expandSearchbar"
    class="rounded-full px-1.5 py-1.5 hover:bg-red-700 hover:text-white sm:hidden"
    :class="[isSearchbarExpanded ? 'hidden' : '']"
  >
    <IconSearch class="h-6 w-6"></IconSearch>
  </button>
</template>
