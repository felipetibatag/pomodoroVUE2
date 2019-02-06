<template>
  <div id="app" class="container border">
    <header>
      <controls-component @fAcciones="fAcciones"></controls-component>
    </header>
    <main>
      <countdown-component :minutos="minutos" :segundos="segundos"></countdown-component>
    </main>
  </div>
</template>

<script>
import ControlsComponent from "./components/ControlsComponent.vue";
import CountdownComponent from "./components/CountdownComponent.vue";
export default {
  name: "app",
  data() {
    return {
      minutos: 0,
      segundos: 0
    };
  },
  components: {
    ControlsComponent,
    CountdownComponent
  },
  methods: {
    fAcciones: function(accion) {
      console.log(accion);
      if (accion == "play") {
        this.timer = setInterval(() => {
          this.segundos++;
          if (this.segundos == 59) {
            this.minutos++;
            this.segundos = 0;
          }
          if (this.segundos < 10) {
            this.segundos = "0" + this.segundos;
          }
          if (this.minutos < 10) {
            this.minutos = this.minutos;
          }
          if (this.minutos == 1) {
            console.log("llego al limite");
            this.segundos = 0;
            this.minutos = 0;
          }
        }, 100);
      }
      if (accion == "pause") {
        console.log("entro por pause");
        clearInterval(this.timer);
      }
      if (accion == "stop") {
        clearInterval(this.timer);
        this.segundos = "0" + 0;
        this.minutos = "0" + 0;
        document.getElementById("btnPause").classList.add("disable");
      }
    },
    fpause: function() {
      clearInterval();
    },
    fstop: function() {
      console.log("stop");
    }
  }
};
</script>