<template>
  <div class="div_container">
    <h1>Leds Options :</h1>
    <div class="ledsOnOff">
      <div class="btns">
        <v-btn color="green" plain elevation="4" v-on:click="pub('L.on')">ON</v-btn>
        <v-btn color="red" plain elevation="4" v-on:click="pub('L.off')">OFF</v-btn>
      </div>
    </div>
    <div class="ledsColor">
      <div class="btns">
        <v-btn color="red" plain elevation="4">RED</v-btn>
        <v-btn color="blue" plain elevation="4">BLUE</v-btn>
        <v-btn color="green" plain elevation="4">GREEN</v-btn>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  methods: {
    pub: function(val) {
      this.$root.publish.payload = val
      this.$root.doPublish()
    },
  },
}
</script>
<style>
.div_container {
  text-align: center;
  max-width: 30%;
  margin: auto;
  margin-top: 20%;
}
.main_card {
  margin-top: 10%;
}
.ledsOnOff {
  display: flex;
  justify-content: space-between;
  width: 50%;
  margin: auto;
}
.ledsColor {
  display: flex;
  justify-content: space-between;
  width: 60%;
  margin: auto;
}
</style>
