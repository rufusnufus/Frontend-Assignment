<template>
  <v-app>
    <v-app-bar 
      app 
      dense 
      color="#142850"
    >
      <h3 class="white--text">Test Task</h3>
    </v-app-bar>

    <v-content>
      <router-view />
    </v-content>

    <v-footer
      color="#142850"
      app
    >
      <span class="white--text">&copy; 2020</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: "App"
};
</script>
