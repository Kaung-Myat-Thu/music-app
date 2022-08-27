<template>
  <Header title="My Music" />
  <Music
    :title="current.title"
    :artist="current.artist"
    :isPlaying="isPlaying"
  />
  <MusicFunction
    @backward="backward"
    @forward="forward"
    @play="play"
    @pause="pause"
    :isPlaying="isPlaying"
  />
  <PlayList :songs="songs" @play="play" :current="current" />
  <Footer text="CopyRight &copy; 2022" />
</template>

<script>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import Music from "./components/Music.vue";
import MusicFunction from "./components/MusicFunction.vue";
import PlayList from "./components/PlayList.vue";
export default {
  name: "App",
  data() {
    return {
      current: {},
      index: 0,
      isPlaying: false,
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
  methods: {
    play(song) {
      if (typeof song.src != "undefined") {
        this.current = song;

        this.player.src = this.current.src;
      }
      this.player.play();
      this.player.addEventListener(
        "ended",
        function () {
          this.index++;
          if (this.index > this.songs.length - 1) {
            this.index = 0;
          }
          this.current = this.songs[this.index];
          this.play(this.current.src);
        }.bind(this)
      );
      this.isPlaying = true;
      // console.log(this.current);
    },
    pause() {
      this.player.pause();
      this.isPlaying = false;
    },
    forward() {
      this.index++;
      if (this.index > this.songs.length - 1) {
        this.index = 0;
      }
      this.current = this.songs[this.index];
      this.play(this.current);
      // console.log(this.index);
    },
    backward() {
      this.index--;
      if (this.index < 0) {
        this.index = this.songs.length - 1;
      }
      this.current = this.songs[this.index];
      this.play(this.current);
    },
  },
  created() {
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
  },
  components: {
    Header,
    Music,
    MusicFunction,
    PlayList,
    Footer,
  },
};
</script>
