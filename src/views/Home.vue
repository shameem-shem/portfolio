<template>
  <div class="home">
    <Banner />
    <div class="home-content">
      <v-container >
        <v-row>
          <v-col cols="2">
            <div class="home-left-wrp">
              <HomeLeft />
            </div>
          </v-col>
          <v-col cols="10">
            <div class="home-right-wrp">
              <v-timeline align-top dense :dark="mode">
                <v-timeline-item
                  v-for="(component,i) in components"
                  :key="i"
                  fillDot
                  color="transparent"
                  fill-dot
                  icon
                  small>
                  <template v-slot:icon>
                    <v-icon medium>$hexagon</v-icon>
                  </template>
                  <component :is="component"></component>
                </v-timeline-item>
              </v-timeline>
            </div>
          </v-col>
        </v-row>
      </v-container>
    </div>
  </div>
</template>

<script>
import Banner from "@/components/Banner";
import HomeLeft from "@/components/HomeLeft";
import About from "@/components/About";
import Qualification from "@/components/Qualification";
import Experiance from "@/components/Experiance";
import Skills from "@/components/Skills";
import Works from "@/components/Works";
import Contact from "@/components/Contact";
// import store from '@/store/index'
// import { mapState } from 'vuex'

export default {
  name: "home",
  data: () => ({
    components: [About, Qualification, Experiance, Skills, Works, Contact]
  }),
  components: {
    Banner,
    HomeLeft,
    About,
    Qualification,
    Skills,
    Works,
    Contact
  },
  computed: {
    mode(){
      return this.$store.state.goDark
    },
  }
};
</script>

<style scoped>
.home section {
  height: calc(100vh - 64px);
}
</style>