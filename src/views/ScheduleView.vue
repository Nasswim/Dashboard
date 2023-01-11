<template>
  <div class="justify-space-around" >
    <Topbar />
    <v-container class="d-inline-flex ">
    <v-row class="col-9">
      <v-col class="col-10">
        <v-card class="mt-3 ml-10" flat>
          <v-tabs fixed-tabs white  >
            <v-tabs-slider color="white"></v-tabs-slider>
            <v-tab class="black--text text-decoration-underline text-capitalize title">
              Recent Added
            </v-tab>
            <v-tab class="grey--text text-capitalize title"> In Progress </v-tab>
            <v-tab class="grey--text text-capitalize title"> In Review </v-tab>
            <v-tab class="grey--text text-capitalize title"> Completed </v-tab>
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
          <v-list-item v-for="(item, i) in listCards" :key="i" class="mt-6 mb-10">
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
        <v-col class="col-10">
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
      </v-col>

    </v-row>
    <v-row class="justify-start col-9 flex-column ">
      <h2 class=" mt-3">Meeting</h2>
      <v-col class=" d-flex">
      <v-list>
        <v-list-item v-for="(item, i) in items" :key="i" class="mt-6 mb-10 d-inline-flex">
          <v-card
              class="mx-auto rounded-xl elevation-8"
              width="130"
              height="250"
              color="#FDF7F2"
              v-bind:class="{ selected: selected }"
              v-on:mouseover="selected = true"
              v-on:mouseout="selected = false"
          >
            <v-card-text>
              <div class="d-flex align-center ma-5 ml-7 flex-column">
                <v-card
                    height="80"
                    width="80"
                    class="rounded-lg mr-3"
                    color="#FBE9E7"
                >
                  <v-card-text class="d-flex align-center justify-center ">
                    <v-icon  >{{ item.title}}</v-icon>
                  </v-card-text>
                </v-card>
                <div class="mr-auto">
                  <p
                      class="text-h7 flex-column"
                      :class="{ 'text--lighten-1': selected }"
                  >
                    {{ item.text }}
                  </p>
                </div>
              </div>
            </v-card-text>
          </v-card>
        </v-list-item>
      </v-list>
      </v-col>

      <v-col class="align-center" >
      <h2 class="ml-15 mb-5 mt-15">Files</h2>
        <v-icon color="black"> mdi-dots-horizontal </v-icon>
        <v-list-item v-for="(item, i) in listCard" :key="i" class="mt-6 mb-10 align-center">
          <v-card
              class="mx-auto rounded-xl elevation-8"
              width="750"
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
                    color="dark"
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
                    <p>{{ item.weight }}</p>
                    <v-icon>{{ item.download }}</v-icon>
                  </div>
              </div>
            </v-card-text>
          </v-card>
        </v-list-item>
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

      items:[
        {
          id: 1,
          title: "Mon 3",
          text: "9:00 AM  2:00 PM  4:00 PM",
        },
        {
          id: 2,
          title: "Tue 4",
          text: "10:30 AM  1:00 PM  ⏤ ",
        },
{
          id: 3,
          title: "Wed 5",
          text: "9:00 AM  3:00 PM  6:00 PM",
        },
        {
          id: 4,
          title: "Thu 6",
          text: "11:00 AM  ⏤ 3:50 PM",
        },
        {
          id: 5,
          title: "Fri 7",
          text: "9:20 AM  1:15 PM  5:45 PM",
        },

      ],

      value1: 65,
      value2: 35,
      selected: false,
      listCard: [
        {
          id: 1,
          icon: "mdi-scale-balance",
          //groupe d'avatar
          heure: "Aug 5 , 2021 at 9:50 AM",
          titre: "User flow.fig",
          weight: '0.6 KB',
          download: 'mdi-folder-download',
        },
        {
          id: 2,
          icon: "mdi-cube",
          //groupe d'avatar
          heure: "Aug 5 , 2021 at 9:20 AM",
          titre: "Design system.fig",
          weight: '0.8 KB',
          download: 'mdi-folder-download',
        },
        {
          id: 3,
          icon: "mdi-file-document-outline",
          //groupe d'avatar
          heure: "Aug 5 , 2021 at 9:05 AM",
          titre: "Animation.json",
          weight: '18 KB',
          download: 'mdi-folder-download',
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
