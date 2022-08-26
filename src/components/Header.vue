<template>
  <div class="bg-gray-500 text-center py-2">
    <h1 class="text-white font-bold text-2xl">{{ title }}</h1>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
  },
};
</script>
