<template>
  <div class="div_container">
    <v-form ref="form" v-model="valid" lazy-validation>
      <v-select v-model="select" :items="items" item-text="dance" item-value="code" label="Select a Preset"></v-select>

      <v-btn :disabled="!valid" color="success" class="mr-4" @click="validate">
        Validate
      </v-btn>
      <v-btn :disabled="valid" color="error" class="mr-4" @click="stop">
        Stop
      </v-btn>
    </v-form>
  </div>
</template>
<script>
export default {
  data: () => ({
    valid: false,
    select: '',
    items: [
      { dance: 'Salute', code: 'P.pose1' },
      { dance: 'Gesticulate', code: 'P.pose2' },
      { dance: 'Whatever', code: 'P.pose3' },
      { dance: 'Hug', code: 'P.hug' },
      { dance: 'Handshake', code: 'P.shankhand' },
      { dance: 'Goodbye', code: 'P.goodbye' },
      { dance: 'Talk 1', code: 'P.talk1' },
      { dance: 'Talk 2', code: 'P.talk2' },
      { dance: 'Talk 3', code: 'P.talk3' },
      { dance: 'Talk 4', code: 'P.talk4' },
      { dance: 'Talk 5', code: 'P.talk5' },
      { dance: 'Talk 6', code: 'P.talk6' },
      { dance: 'Talk 7', code: 'P.talk7' },
      { dance: 'Talk 8', code: 'P.talk8' },
      { dance: 'Nod', code: 'P.nod' },
      { dance: 'Clap', code: 'P.applause' },
      { dance: 'Scratch head', code: 'P.zhuatou' },
      { dance: 'Walk right', code: 'P.guideright' },
      { dance: 'Walk left', code: 'P.guideleft' },
      { dance: 'Cute', code: 'P.cute' },
      { dance: 'Fight', code: 'P.fendou' },
      { dance: 'Grow', code: 'P.zhanggao' },
      { dance: 'Swing arms', code: 'P.swingarm' },
      { dance: 'Search', code: 'P.searching' },
      { dance: 'Zone out', code: 'P.fadai' },
      { dance: 'Survey', code: 'P.tiaowang' },
      { dance: 'Grab', code: 'P.longzhuashou' },
      { dance: 'Protect', code: 'P.baohu' },
      { dance: 'Wonder', code: 'P.suprise' },
      { dance: 'Guide', code: 'P.zhilu' },
      { dance: 'Shy', code: 'P.shy' },
      { dance: 'Conduct', code: 'P.command' },
      { dance: 'End conducting', code: 'P.commandover' },
      { dance: 'Walk', code: 'P.walk' },
    ],
  }),
  methods: {
    pub: function() {
      this.$root.publish.payload = this.select
      this.$root.doPublish()
    },
    validate() {
      this.$refs.form.validate()
      if (this.select != '') {
        this.valid = false
        this.pub()
      }
    },
    stop() {
      this.$root.publish.payload = 'D.stop'
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
