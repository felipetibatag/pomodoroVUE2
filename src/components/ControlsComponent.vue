<template>
  <div class="row">
    <div class="col-md-5">
      <h1 class="display-1 col-md-3">Pomodoro</h1>
    </div>
    <div class="col" style="fontSize:2em">
      <button id="btnPlay">
        <i id="play" class="fas fa-play pt-5 mt-auto" style="padding-left:1em" @click="fPlay"></i>
      </button>
      <button id="btnPause">
        <i id="pause" class="fas fa-pause pt-5 mt-auto" style="padding-left:1em" @click="fPause"></i>
      </button>
      <button id="btnStop">
        <i id="stop" class="fas fa-stop pt-5 mt-auto" style="padding-left:1em" @click="fStop"></i>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      play: { activo: false },
      pause: { activo: false },
      stop: { activo: false }
    };
  },
  methods: {
    cambiaColor: function($event) {
      let el = $event.currentTarget.id;
      document.getElementById(el).classList.toggle("text-success");
    },
    fPlay: function($event) {
      this.cambiaColor($event);
      event.currentTarget.removeEventListener("click", this.fplay);
      this.$emit("fAcciones", "play");
      console.log("tiempo inicia");
    },
    fPause: function($event) {
      this.cambiaColor($event);
      this.$emit("fAcciones", "pause");
      console.log("tiempo pausa");
    },
    fStop: function($event) {
      this.cambiaColor($event);
      this.$emit("fAcciones", "stop");
      console.log("tiempo Para");
    }
  }
};
</script>

<style>
</style>
