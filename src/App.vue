<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
        <router-link to="/"
          ><v-btn depressed x-large text>
            <v-img alt="Vuetify Name" class="shrink mt-1" contain min-width="100" src="./assets/logo.png" width="125" />
          </v-btn>
        </router-link>
      </div>
      <v-spacer></v-spacer>
      <h1>CRUZR UI</h1>
      <v-spacer></v-spacer>
      <v-btn>Connected</v-btn>
    </v-app-bar>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  mounted() {
    this.$root.createConnection()

  },
}
</script>
