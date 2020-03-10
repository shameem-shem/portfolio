<template>
  <div class="home-left">
    <v-card height="400" width="256" class="mx-auto" :dark="mode">
      <v-navigation-drawer permanent>
        <v-list dense nav>
          <v-list-item
            v-for="(item,i) in items"
            :key="i" link
            @click="$vuetify.goTo(item.trgt, options)">
            <v-list-item-icon class="mr-4">
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title>{{ item.text }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
    </v-card>
  </div>
</template>

<script>
export default {
  data: () => ({
    item: 1,
    items: [
      { text: "About Me", trgt: "#about", icon: "$hexagon"},
      { text: "Education", trgt: "#qualification", icon: "$hexagon" },
      { text: "Experiance", trgt: "#experiance", icon: "$hexagon" },
      { text: "Skills", trgt: "#skills", icon: "$hexagon" },
      { text: "My Works", trgt: "#works", icon: "$hexagon" },
      { text: "Contact Me", trgt: "#contact", icon: "$hexagon" }
    ]
  }),
  computed: {
    mode(){
      return this.$store.state.goDark
    },
    options() {
      return {
        duration: 800,
        offset: 0,
        easing: 'easeInOutCubic'
      };
    }
  }
};
</script>

<style scoped>
</style>