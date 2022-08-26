<template>
  <Header title="My Music" />
  <Music :title="current.title" :artist="current.artist" />
  <MusicFunction @play="play" @pause="pause" :isPlaying="isPlaying" />
</template>

<script>
import Header from "./components/Header.vue";
import Music from "./components/Music.vue";
import MusicFunction from "./components/MusicFunction.vue";
export default {
  name: "App",
  data() {
    return {
      index: 0,
      isPlaying: false,
      current: {},
      songs: [
        {
          title: "Grateful",
          artist: "Neffx",
          src: require("./assets/neffex-grateful.mp3"),
        },
        {
          title: "Invicible",
          artist: "Deaf Kev",
          src: require("./assets/deaf-kev-invincible.mp3"),
        },
      ],
      player: new Audio(),
    };
  },
  created() {
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
  },
  methods: {
    play(song) {
      if (typeof this.songs.src != "undefined") {
        this.current = song;

        this.player.src = this.current.src;
      }
      this.player.play();
      this.isPlaying = true;
      console.log("click");
    },
    pause() {
      this.player.pause();
      this.isPlaying = false;
      // console.log("click");
    },
  },
  components: {
    Header,
    Music,
    MusicFunction,
  },
};
</script>
