<template>
  <div class="max-w-sm mx-auto mt-4 flex justify-around items-center">
    <div
      class="hover:bg-gray-200 px-4 py-3 bg-gray-300 rounded-full text-center"
    >
      <button class="cursor-pointer"><i class="fas fa-backward"></i></button>
    </div>
    <div
      class="hover:bg-gray-200 px-5 py-3 bg-gray-300 rounded-full text-center"
    >
      <button v-if="!isPlaying" @click="$emit('play')" class="cursor-pointer">
        <i class="fas fa-play"></i>
      </button>
      <button v-else @click="$emit('pause')" class="cursor-pointer">
        <i class="fas fa-pause"></i>
      </button>
    </div>
    <div
      class="hover:bg-gray-200 px-4 py-3 bg-gray-300 rounded-full text-center"
    >
      <button class="cursor-pointer"><i class="fas fa-forward"></i></button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["isPlaying"],
};
</script>
