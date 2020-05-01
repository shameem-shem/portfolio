<template>
  <v-app-bar app :dark="mode">
    <router-link to="/">
      <v-icon large style="width:36px">$logo</v-icon>
    </router-link>
    <v-spacer></v-spacer>
    <v-btn outlined color="primary">
      <router-link to="/login">Login</router-link>
    </v-btn>
    <v-btn outlined color="primary" class="ml-4">
      <router-link to="/dashboard">Dashboard</router-link>
    </v-btn>
    <!-- <router-link to="/register">Register</router-link> -->
      <v-switch v-model="$store.state.goDark"  class="mt-3 ml-4"></v-switch>
  </v-app-bar>
</template>

<script>
// import store from '../store/index';
export default {
  data(){
    return{
      // goDark: false
    }
  },
  computed:{
    mode(){
      return this.$store.state.goDark
    }
  }
}
</script>

<style scoped>
a{
  text-decoration: none
}
.theme--dark svg{
  fill: #fff;
}
</style>