<script setup>
defineProps({
  title: {
    type: String,
    default: "Title",
  },
  rating: {
    type: String,
    default: "0",
  },
});
</script>

<template>
  <div
    class="relative flex shrink-0 basis-[250px] flex-col overflow-hidden rounded-xl shadow-lg"
  >
    <img
      src="https://cdn.shopify.com/s/files/1/0057/3728/3618/products/108b520c55e3c9760f77a06110d6a73b_240x360_crop_center.progressive.jpg?v=1573652543"
      alt=""
    />
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
      {{ rating }}
    </div>
  </div>
</template>
