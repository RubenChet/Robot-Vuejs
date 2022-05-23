<template>
  <div class="div_container">
    <v-form ref="form" lazy-validation>
      <div class="the_slider">
        <v-slider
          v-model="slide.val"
          :label="slide.label"
          :thumb-color="slide.color"
          thumb-label="always"
          :max="slide.max"
          :min="slide.min"
        ></v-slider>
        <template>
          <img src="../assets/info.png" @click.stop="dialog = true" />

          <v-dialog v-model="dialog" max-width="290">
            <v-card>
              <v-card-title class="text-h5">
                Use Google's location service?
              </v-card-title>

              <v-card-text>
                Let Google help apps determine location. This means sending anonymous location data to Google, even when
                no apps are running.
              </v-card-text>

              <v-card-actions>
                <v-spacer></v-spacer>

                <v-btn color="green darken-1" text @click="dialog = false">
                  Disagree
                </v-btn>

                <v-btn color="green darken-1" text @click="dialog = false">
                  Agree
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-dialog>
        </template>
      </div>

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
    slide: { label: 'Head Motion', val: 0, min: -15, max: 15 },
    value: 0,
    dialog: false,
  }),

  methods: {
    pub: function() {
      if (this.slide.val > 0) {
        this.value = -Math.abs(this.slide.val)
      } else {
        this.value = Math.abs(this.slide.val)
      }
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
  max-width: 35%;
  margin: auto;
  margin-top: 20%;
}
.the_slider {
  display: flex;
  justify-content: space-between;
}
img {
  margin-top: 0.8%;
  max-width: 20px;
  max-height: 20px;
}
</style>
