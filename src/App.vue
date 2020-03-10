<template>
  <v-app :class="mode ? 'theme--dark' : 'theme--light'">
    
    <Header />

    <v-content >
      <router-view></router-view>
    </v-content>

    <v-footer :dark="mode">
      <p class="mb-0">Designed and developed by Shameem</p>
      <v-spacer></v-spacer>
      <div>&copy; {{ new Date().getFullYear() }} Shemfolio</div>
    </v-footer>
  </v-app>
</template>

<script>
import Header from '@/components/Header'
export default {
  name: "App",

  components: {
    Header
  },

  data() {
    return {
      // goDark: false
    };
  },
  computed:{
    mode(){
      return this.$store.state.goDark
    }
  }
};
</script>

<style lang="scss">
@import 'scss/variables.scss';
  
</style>
