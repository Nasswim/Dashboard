<template>
  <div>
    <Topbar />
    <v-row>
      <v-col class="col-7">
        <v-card class="mt-3 ml-10" flat>
          <v-tabs fixed-tabs white>
            <v-tabs-slider color="white"></v-tabs-slider>
            <v-tab class="black--text text-decoration-underline text-capitalize">
              Recent Added
            </v-tab>
            <v-tab class="grey--text text-capitalize"> In Progress </v-tab>
            <v-tab class="grey--text text-capitalize"> In Review </v-tab>
            <v-tab class="grey--text text-capitalize"> Completed </v-tab>
          </v-tabs>
        </v-card>
        <v-list class="mb-4">
          <v-card
            class="mx-auto rounded-xl"
            width="600"
            color="black"
            height="150"
            v-bind:class="{ selected: selected }"
            v-on:mouseover="selected = true"
            v-on:mouseout="selected = false"
          >
            <v-card-text>
              <div class="d-flex align-center ma-5 ml-7">
                <v-card
                  height="65"
                  width="65"
                  class="rounded-lg mr-5"
                  color="white"
                >
                  <v-card-text class="d-flex align-center justify-center">
                    <v-icon large color="black">mdi-cookie-alert</v-icon>
                  </v-card-text>
                </v-card>
                <div class="mr-auto">
                  <h2 class="white--text mt-3">Illustation Templates</h2>
                  <p class="mt-3 grey--text">9:00 AM - 4:00 PM</p>
                </div>
                <div class="text--primary d-flex">
                  <div>
                    <v-avatar>
                      <img src="https://cdn.vuetifyjs.com/images/lists/1.jpg" />
                    </v-avatar>
                    <v-avatar>
                      <img src="https://cdn.vuetifyjs.com/images/lists/3.jpg" />
                    </v-avatar>
                    <v-avatar>
                      <img src="https://cdn.vuetifyjs.com/images/lists/2.jpg" />
                    </v-avatar>
                  </div>
                </div>
              </div>
            </v-card-text>
          </v-card>
          <v-list-item v-for="(item, i) in listeCards" :key="i" class="mt-6 mb-10">
            <v-card
              class="mx-auto rounded-xl elevation-8"
              width="600"
              height="150"
              v-bind:class="{ selected: selected }"
              v-on:mouseover="selected = true"
              v-on:mouseout="selected = false"
            >
              <v-card-text>
                <div class="d-flex align-center ma-5 ml-7">
                  <v-card
                    height="65"
                    width="65"
                    class="rounded-lg mr-5"
                    color="#FBE9E7"
                  >
                    <v-card-text class="d-flex align-center justify-center">
                      <v-icon large color="black">{{ item.icon }}</v-icon>
                    </v-card-text>
                  </v-card>
                  <div class="mr-auto">
                    <p
                      class="text-h5 text--primary"
                      :class="{ 'text--lighten-1': selected }"
                    >
                      {{ item.titre }}
                    </p>
                    <p>{{ item.heure }}</p>
                  </div>
                  <div class="text--primary d-flex">
                    <div v-for="avatar in item.avatar" :key="avatar.id">
                      <v-avatar class="mr-2">
                        <img :src="avatar.src" />
                      </v-avatar>
                    </div>
                  </div>
                </div>
              </v-card-text>
            </v-card>
          </v-list-item>
        </v-list>
        <v-row id="dot" justify="end">
          <v-icon color="black"> mdi-dots-horizontal </v-icon>
        </v-row>
        <h2 class="ml-15 mb-5 mt-15">Project Progress</h2>
        <v-card
          class="ml-15 elevation-0"
          color="grey lighten-4"
          width="600"
          height="350"
        >
          <v-row>
            <h3 class="ma-3 ml-10">Illustration Template</h3>
            <v-row class="mr-10 mt-2" justify="end">
              <v-icon class="mr-5" color="black">mdi-folder-download</v-icon>
              <v-icon color="black">mdi-pencil-box</v-icon>
            </v-row>
          </v-row>
          <v-row class="mt-5" justify="center">
            <apexchart
              width="450"
              type="donut"
              :options="options"
              :series="series"
            ></apexchart>
          </v-row>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script lang="ts">
import Topbar from "@/components/Topbar.vue";

export default {
  name: "ScheduleView",
  components: {
    Topbar,
  },
  data() {
    return {
      value1: 65,
      value2: 35,
      selected: false,
      listeCards: [
        {
          id: 1,
          icon: "mdi-scale-balance",
          //groupe d'avatar
          avatar: [
            {
              id: 1,
              src: "https://cdn.vuetifyjs.com/images/lists/1.jpg",
            },
            {
              id: 2,
              src: "https://cdn.vuetifyjs.com/images/lists/2.jpg",
            },
          ],
          heure: "4:00 PM - 5:00 PM",
          titre: "UI Design",
        },
        {
          id: 2,
          icon: "mdi-cube",
          //groupe d'avatar
          avatar: [
            {
              id: 1,
              src: "https://cdn.vuetifyjs.com/images/lists/1.jpg",
            },
            {
              id: 2,
              src: "https://cdn.vuetifyjs.com/images/lists/2.jpg",
            },
            {
              id: 3,
              src: "https://cdn.vuetifyjs.com/images/lists/3.jpg",
            },
          ],
          heure: "5:00 PM - 6:00 PM",
          titre: "UX Design",
        },
      ],
      options: {
        labels: ["Cartoon Illustation", "Abstract Pattern"],
        colors: ["#E65100", "#000000"],
      },
      series: [35, 65],
    };
  },
};
</script>

<style>
.selected {
  background-color: #000;
}

.selected .text--primary {
  color: #fff;
}

#dot {
  margin-bottom: -13%;
  margin-right: 10%;
}
</style>
