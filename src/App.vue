<template>
  <v-app id="app">
  <v-content>
  <v-container fluid fill-height>
  <v-layout align-center justify-center>
    <v-flex xs12 sm8 md4>
      <v-card class="elevation-12">
        <v-toolbar dark color="primary">
          <v-toolbar-title>Lunch Picker</v-toolbar-title>
        </v-toolbar>
              <v-card-text>
        <lunch-picker/>
        <h5>โดย นายพนธกร แพแสง</h5>
      </v-card-text>
      </v-card>
    </v-flex>
  </v-layout>
  </v-container>
  </v-content>
  </v-app>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import LunchPicker from './components/LunchPicker.vue'
export default {
  name: 'app',
  components: {
    LunchPicker
  }
}
</script>

<style>
#app {
  font-family: 'Roboto', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
