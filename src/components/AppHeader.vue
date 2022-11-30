<script setup>
import SearchBar from "./SearchBar.vue";
import IconHamburgerMenu from "./Icons/IconHamburgerMenu.vue";
import { ref } from "vue";

const isSearchbarExpanded = ref(false);
</script>

<template>
  <header class="shadow-lg">
    <nav class="mx-auto flex max-w-7xl items-center px-4 py-4">
      <div
        class="flex shrink-0 space-x-8"
        :class="[isSearchbarExpanded ? 'hidden' : '']"
      >
        <RouterLink to="/">
          <img src="../assets/moviesbucket-logo.svg" alt="" />
        </RouterLink>
        <ul class="hidden items-center space-x-4 font-bold sm:flex">
          <li>Movies</li>
          <li>Series</li>
        </ul>
      </div>
      <div
        class="ml-auto flex w-full justify-end space-x-4 sm:max-w-lg sm:pl-8"
      >
        <SearchBar
          @expand-searchbar="isSearchbarExpanded = true"
          @close-searchbar="isSearchbarExpanded = false"
        >
        </SearchBar>
        <button class="sm:hidden">
          <IconHamburgerMenu class="h-8 w-8"></IconHamburgerMenu>
        </button>
      </div>
    </nav>
  </header>
</template>

<style></style>
