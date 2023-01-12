<template>
  <div class="justify-space-around">
    <Topbar />
    <v-container class="d-inline-flex">
      <v-row>
        <v-col cols="6">
          <v-row justify="center">
            <v-col cols="10">
              <v-card class="mt-3" min-width="100%" flat>
                <v-tabs fixed-tabs white>
                  <v-tabs-slider color="white"></v-tabs-slider>
                  <v-tab
                    class="black--text text-decoration-underline text-capitalize title"
                  >
                    Recent Added
                  </v-tab>
                  <v-tab class="grey--text text-capitalize title">
                    In Progress
                  </v-tab>
                  <v-tab class="grey--text text-capitalize title">
                    In Review
                  </v-tab>
                  <v-tab class="grey--text text-capitalize title">
                    Completed
                  </v-tab>
                </v-tabs>
              </v-card>
            </v-col>
          </v-row>

          <v-row justify="center">
            <v-col cols="10">
              <v-list class="mb-4">
                <v-card
                  class="mx-auto rounded-xl"
                  width="95%"
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
                            <img
                              src="https://cdn.vuetifyjs.com/images/lists/1.jpg"
                            />
                          </v-avatar>
                          <v-avatar>
                            <img
                              src="https://cdn.vuetifyjs.com/images/lists/3.jpg"
                            />
                          </v-avatar>
                          <v-avatar>
                            <img
                              src="https://cdn.vuetifyjs.com/images/lists/2.jpg"
                            />
                          </v-avatar>
                        </div>
                      </div>
                    </div>
                  </v-card-text>
                </v-card>
                <v-list-item
                  v-for="(item, i) in listCards"
                  :key="i"
                  class="mt-6 mb-10"
                  width="100%"
                >
                  <v-card
                    class="mx-auto rounded-xl elevation-8"
                    width="95%"
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
                          <v-card-text
                            class="d-flex align-center justify-center"
                          >
                            <v-icon large color="black">{{ item.icon }}</v-icon>
                          </v-card-text>
                        </v-card>
                        <div class="mr-auto">
                          <p
                            class="text-h5 text--primary font-weight-bold"
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
            </v-col>
          </v-row>

          <v-row justify="center">
            <v-col cols="10">
              <v-row justify="space-between" class="mb-9">
                <h2>Project Progress</h2>
                <v-icon color="black"> mdi-dots-horizontal </v-icon>
              </v-row>
              <v-row justify="center">
                <v-card
                  class="elevation-0"
                  color="grey lighten-4"
                  width="95%"
                  rounded="rounded"
                >
                  <v-card-text>
                    <v-row justify="space-between" class="pa-6">
                      <h3 class="black--text">Illustration Template</h3>
                      <div>
                        <v-icon class="mr-5" color="black"
                          >mdi-folder-download</v-icon
                        >
                        <v-icon color="black">mdi-pencil-box</v-icon>
                      </div>
                    </v-row>
                    <v-row justify="center">
                      <apexchart
                        width="450"
                        type="donut"
                        :options="options"
                        :series="series"
                        class="mb-5"
                      ></apexchart>
                    </v-row>
                  </v-card-text>
                </v-card>
              </v-row>
            </v-col>
          </v-row>
        </v-col>

        <v-col cols="6">
          <v-container>
            <v-row class="mb-15" justify="center">
              <div>
                <v-row class="py-9" align="center" justify="space-between">
                  <h3 style="font-size: 25px">Meeting</h3>
                  <div class="mr-3">
                    <span class="mr-3 font-weight-bold" style="font-size: 18px">Aug 3, 2021 - Aug 7, 2021</span>
                    <v-icon color="black">mdi-menu-down-outline</v-icon>
                  </div>
                </v-row>
                <v-row>
                  <v-card color="#FDF7F2" class="rounded-xl">
                    <v-card-text>
                      <v-list color="transparent">
                        <v-list-item
                          v-for="(item, i) in items"
                          :key="i"
                          class="mt-6 mb-10 d-inline-flex"
                          style="max-width: 20%"
                        >
                          <v-card
                            class="rounded-xl elevation-0"
                            height="350"
                            color="transparent"
                            v-bind:class="{ selected: selected }"
                            v-on:mouseover="selected = true"
                            v-on:mouseout="selected = false"
                          >
                            <v-card-text>
                              <div class="d-flex flex-column">
                                <v-card
                                  width="80"
                                  class="rounded-lg mb-6"
                                  color="#FBE9E7"
                                >
                                  <v-card-text
                                    class="d-flex align-center justify-center"
                                  >
                                    <span
                                      class="text-center font-weight-bold"
                                      style="
                                        font-size: 25px;
                                        line-height: 34px;
                                        color: black;
                                      "
                                      >{{ item.title }}</span
                                    >
                                  </v-card-text>
                                </v-card>
                                <div class="text-center mb-12">
                                  <p class="text-h7 font-weight-bold">
                                    {{ item.text1 }}
                                  </p>
                                </div>
                                <div class="text-center mb-12">
                                  <p class="text-h7 font-weight-bold">
                                    {{ item.text2 }}
                                  </p>
                                </div>
                                <div class="text-center">
                                  <p class="text-h7 font-weight-bold">
                                    {{ item.text3 }}
                                  </p>
                                </div>
                              </div>
                            </v-card-text>
                          </v-card>
                        </v-list-item>
                      </v-list>
                    </v-card-text>
                  </v-card>
                </v-row>
              </div>
            </v-row>
          </v-container>

          <v-container>
            <v-row class="mt-10" justify="center">
              <div style="min-width: 95%">
                <v-row class="mb-3" align="center" justify="space-between">
                  <h2 class="ml-4" style="font-size: 25px">Files</h2>
                  <span class="font-weight-bold mr-4" style="font-size: 18px"
                    >View all
                    <v-icon color="black">mdi-arrow-right</v-icon>
                  </span>
                </v-row>

                <v-list-item
                  v-for="(item, i) in listCard"
                  :key="i"
                  class="mt-6 mb-10 pa-0 align-center"
                >
                  <v-card
                    style="border: 2px solid black"
                    class="rounded-xl elevation-0"
                    width="100%"
                    height="150"
                    v-bind:class="{ selected: selected }"
                    v-on:mouseover="selected = true"
                    v-on:mouseout="selected = false"
                  >
                    <v-card-text>
                      <div class="d-flex align-center ma-5 ml-7">
                        <v-card
                          style="background-color: #1e1e1e"
                          height="65"
                          width="65"
                          class="rounded-lg mr-5"
                          color="dark"
                        >
                          <v-card-text
                            class="pa-0 d-flex align-center justify-center"
                          >
                            <v-img src="../assets/logo-figma.png" large color="black"/> 
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
                        <div align="center" class="text--primary d-flex">
                          <span style="font-size: 20px" class="mr-5">{{
                            item.weight
                          }}</span>
                          <v-icon>{{ item.download }}</v-icon>
                        </div>
                      </div>
                    </v-card-text>
                  </v-card>
                </v-list-item>
              </div>
            </v-row>
          </v-container>
        </v-col>
      </v-row>
    </v-container>
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
      items: [
        {
          id: 1,
          title: "Mon 3",
          text1: "9:00 AM",
          text2: "2:00 PM",
          text3: "4:00 PM",
        },
        {
          id: 2,
          title: "Tue 4",
          text1: "10:30 AM",
          text2: "1:00 PM",
          text3: "⏤",
        },
        {
          id: 3,
          title: "Wed 5",
          text1: "9:00 AM",
          text2: "3:00 PM",
          text3: "6:00 PM",
        },
        {
          id: 4,
          title: "Thu 6",
          text1: "11:00 AM",
          text2: "⏤",
          text3: "3:50 PM",
        },
        {
          id: 5,
          title: "Fri 7",
          text1: "9:20 AM",
          text2: "1:15 PM",
          text3: "5:45 PM",
        },
      ],

      value1: 65,
      value2: 35,
      selected: false,
      listCard: [
        {
          id: 1,
          icon: "../assets/logo-figma.png",
          //groupe d'avatar
          heure: "Aug 5 , 2021 at 9:50 AM",
          titre: "User flow.fig",
          weight: "0.6 KB",
          download: "mdi-folder-download",
        },
        {
          id: 2,
          icon: "../assets/logo-figma.png",
          //groupe d'avatar
          heure: "Aug 5 , 2021 at 9:20 AM",
          titre: "Design system.fig",
          weight: "0.8 KB",
          download: "mdi-folder-download",
        },
        {
          id: 3,
          icon: "../assets/logo-json.png",
          //groupe d'avatar
          heure: "Aug 5 , 2021 at 9:05 AM",
          titre: "Animation.json",
          weight: "18 KB",
          download: "mdi-folder-download",
        },
      ],
      listCards: [
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
