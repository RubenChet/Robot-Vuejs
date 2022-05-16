<template>
  <div class="div_container">
    <v-form ref="form" lazy-validation>
      <v-slider
        v-model="slide.val"
        :label="slide.label"
        :thumb-color="slide.color"
        thumb-label="always"
        :max="slide.max"
        :min="slide.min"
      ></v-slider>
      <v-btn color="success" class="mr-4" @click="validate">
        Validate
      </v-btn>

      <v-btn color="error" class="mr-4" @click="reset">
        Reset Head
      </v-btn>
    </v-form>
  </div>
</template>
<script>
export default {
  data: () => ({
    slide: { label: 'Head Motion', val: 0, min: -50, max: 50 },
    value: 0,
  }),

  methods: {
    pub: function() {
      this.value = -Math.abs(this.slide.val)
      this.$root.publish.payload = 'H.' + this.value
      this.$root.doPublish()
    },
    validate() {
      this.$refs.form.validate()
      if (this.text != '') {
        this.pub()
      }
    },
    reset() {
      this.$root.publish.payload = 'P.reset'
      this.$root.doPublish()
      this.$refs.form.reset()
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
</style>
