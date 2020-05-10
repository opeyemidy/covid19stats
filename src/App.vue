<template>
  <v-app>
    <v-app-bar app dark>
      <div class="d-flex align-center">
        <div class="title">
          Ritzy
        </div>
      </div>

      <v-spacer></v-spacer>

      <div></div>
    </v-app-bar>

    <v-content>
      <router-view></router-view>
    </v-content>
  </v-app>
</template>

<script>
// import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',

  components: {
    // HelloWorld
  },

  data: () => ({
    //
  })
}
</script>
