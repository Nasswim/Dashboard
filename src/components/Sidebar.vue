<template>
  <div>
      <v-navigation-drawer width="235" class="black align-center noscroll" app dark permanent>
        <v-avatar class="ma-5">
          <img src="@/assets/logo.png" alt="logo" />
        </v-avatar>
        <v-list class="mt-7">
          <v-list-item v-bind:class="{'white--text': item.path === $route.path}" class="mb-5" v-for="item in items" :key="item.title" link :to="item.path">
            <v-list-item-icon>
              <v-icon color="grey">{{ item.icon }}</v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title class="grey--text">{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>

        <template v-slot:append>
          <div class="mb-10">
            <v-btn class="text-capitalize" text>
              <v-icon class="mr-3"> mdi-logout </v-icon>
              Logout
            </v-btn>
          </div>
        </template>
      </v-navigation-drawer>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "Sidebar",
  data() {
    return {
      items: [
        { title: "Profile", icon: "mdi-account", path:'/profile'},
        { title: "Schedule", icon: "mdi-calendar-month", path:'/schedule' },
        { title: "Overview", icon: "mdi-chart-box", path:'/overview'},
        { title: "Chat", icon: "mdi-chat-processing", path:'/chat' },
        { title: "Settings", icon: "mdi-cog", path:'/settings' },
      ],
    };
  },
});
</script>

<style scoped>
  .noscroll {
    overflow-y: hidden;
  }
</style>
