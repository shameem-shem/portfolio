<template>
  <div class="dashboard">
    <v-container>
      <v-card class="my-12">
        <v-toolbar flat color="primary" dark>
          <v-toolbar-title>{{this.tabs[active_tab].title}}</v-toolbar-title>
        </v-toolbar>
        <v-tabs :vertical="(this.windowWidth > 800) ? true : false" class="py-md-10" v-model="active_tab">
          <v-tab v-for="tab in tabs" :key="tab.tabId">
            <v-icon left>{{tab.icon}}</v-icon>
            {{tab.subtitle}}
          </v-tab>

          <v-tab-item v-for="tab in tabs" :key="tab.tabId" class="px-8">
            <v-card flat>
              <v-card-text class="px-5 py-0">
                <component :is="tab.component"></component>
              </v-card-text>
            </v-card>
          </v-tab-item>
        </v-tabs>
      </v-card>
    </v-container>
  </div>
</template>

<script>
import DashboardProfile from "@/components/DashboardProfile";
import DashboardSkills from "@/components/DashboardSkills";
import DashboardWorks from "@/components/DashboardWorks";
import DashboardExperiance from "@/components/DashboardExperiance";
import DashboardMessages from "@/components/DashboardMessages";
import DashboardPassword from "@/components/DashboardPassword";

export default {
  data() {
    return {
      vertical: false,
      windowWidth: 0,
      tabs: [
        {
          tabId: "0",
          subtitle: "Profile",
          icon: "mdi-account-outline",
          title: "Edit Profile & Password",
          component: DashboardProfile
        },
        {
          tabId: "1",
          subtitle: "Skills",
          icon: "mdi-xml",
          title: "Add Work Skills",
          component: DashboardSkills
        },
        {
          tabId: "2",
          subtitle: "Experiance",
          icon: "mdi-xml",
          title: "Add Work Experiance",
          component: DashboardSkills
        },
        {
          tabId: "3",
          subtitle: "Works",
          icon: "mdi-wan",
          title: "Manage works",
          component: DashboardWorks
        },
        {
          tabId: "4",
          subtitle: "Messages",
          icon: "mdi-message-text-outline",
          title: "Manage Messages",
          component: DashboardMessages
        },
         {
          tabId: "5",
          subtitle: "Password",
          icon: "mdi-message-text-outline",
          title: "Change Password",
          component: DashboardPassword
        }
      ],
      active_tab: '0'
    };
  },
  components: {
    DashboardProfile,
    DashboardSkills,
    DashboardExperiance,
    DashboardWorks,
    DashboardMessages,
    DashboardPassword
  },
  created() {
    window.addEventListener("resize", this.handleResize);
    this.handleResize();
  },
  destroyed() {
    window.addEventListener("resize", this.handleResize);
  },
  methods: {
    handleResize() {
      this.windowWidth = window.innerWidth;
    },
    // activeTab(){
    //   console.log(this.active_tab);
    //   return this.active_tab;
    // }
  }
};
</script>

<style scoped lang="scss">
.dashboard{
  .v-tab{
    @media (min-width: 800px){
      text-align: left;
      justify-content: flex-start;
    }
  }
}
</style>