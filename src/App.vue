<script setup>
import { RouterView } from "vue-router";
import AppHeader from "./components/AppHeader.vue";
</script>

<template>
  <AppHeader></AppHeader>
  <RouterView v-slot="{ Component }">
    <Suspense timeout="1000">
      <template #default>
        <component :is="Component" />
      </template>
      <template #fallback>
        <div
          class="flex h-[calc(100vh-68px)] items-center justify-center text-7xl font-bold"
        >
          Loading...
        </div>
      </template>
    </Suspense>
  </RouterView>
</template>

<style scoped></style>
