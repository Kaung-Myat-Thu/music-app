<template>
  <div class="max-w-md mx-auto text-center mt-4">
    <div
      class="w-24 h-24 bg-gray-300 rounded-full mx-auto border-8 border-gray-500"
      :class="isPlaying ? 'animate-pulse' : ''"
    ></div>
    <div class="my-4">
      <span class="text-lg font-semibold">{{ title }}</span> -
      <span class="text-lg font-semibold">{{ artist }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: ["title", "artist", "isPlaying"],
};
</script>

<style></style>
