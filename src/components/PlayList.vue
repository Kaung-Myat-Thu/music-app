<template>
  <div class="max-w-md mx-auto my-4">
    <h3 class="text-2xl font-semibold">PlayLists</h3>
    <div>
      <button
        v-for="song in songs"
        :key="song.src"
        class="bg-gray-300 px-4 py-2 w-full my-2 rounded-sm hover:bg-gradient-to-tr from-slate-300 to-gray-300"
        :class="
          song.src == current.src
            ? 'bg-gradient-to-r from-slate-400 to-gray-400 text-white'
            : ''
        "
        @click="$emit('play', song)"
      >
        {{ song.title }} - {{ song.artist }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["songs", "current"],
};
</script>
