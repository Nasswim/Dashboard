<template>
  <div>
    <v-row>
    <h1 class="ml-15 mt-13">Schedule</h1>

    </v-row>
    <v-row >
      <v-col class="col-6">
      <v-card class="mt-3 ml-10 " flat>
        <v-tabs
            fixed-tabs
            white

        >
          <v-tab>
            Recent Added
          </v-tab>
          <v-tab>
            In Progress
          </v-tab>
          <v-tab>
            In Review
          </v-tab>
          <v-tab>
            Completed
          </v-tab>
        </v-tabs>
      </v-card>
        <v-list class="mt-6 mb-4 ">
          <v-list-item v-for="(item,i) in listeCards" :key="i" class="mt-6"

          >
            <v-card class="mx-auto rounded-xl " width="600" height="150"
                    v-bind:class="{ 'selected': selected }" v-on:mouseover="selected = true" v-on:mouseout="selected = false"
            >
              <v-card-text>
                <div class="d-flex align-center ma-5 ml-7">
                <v-card
                height="65"
                width="65"
                class="rounded-lg mr-5 "
                color="#FBE9E7"
                >
                  <v-card-text class="d-flex align-center justify-center">
                    <v-icon class="display-1">{{item.icon}}</v-icon>
                  </v-card-text>
                </v-card>
                  <div class="mr-auto">
                    <p class="text-h5 text--primary" :class="{ 'text--lighten-1': selected }">{{item.titre}}</p>
                    <p>{{item.heure}}</p>
                  </div>
                  <div class="text--primary d-flex">
                    <div v-for="avatar in item.avatar" :key="avatar.id">
                      <v-avatar class="mr-2">
                        <img :src="avatar.src" :alt="avatar.alt" />
                      </v-avatar>
                    </div>
                  </div>
                </div>
              </v-card-text>
            </v-card>
          </v-list-item>
        </v-list>

        <h2 class="ma-15">Project Progress</h2>
        <v-card
        class="mx-auto " width="600" height="350"
        >
          <h3 class="headline ">Illustration Template </h3>

        </v-card>
      </v-col>


    </v-row>

  </div>
</template>

<script>
export default {
  data() {
    return {
      value1: 65,
      value2: 35,
      selected: false,
      listeCards : [
        {
          id: 1,
          icon: 'mdi-cookie-edit',
          //groupe d'avatar
          avatar: [
            {
              id: 1,
              src: 'https://cdn.vuetifyjs.com/images/lists/1.jpg',
            },
            {
              id: 2,
              src: 'https://cdn.vuetifyjs.com/images/lists/2.jpg',
            },
            {
              id: 3,
              src: 'https://cdn.vuetifyjs.com/images/lists/3.jpg',
            },
          ],
          heure: '9:00 AM - 4:00 PM',
          titre: 'Illustration Templates',
        },
        {
          id: 2,
          icon: 'mdi-account',
          //groupe d'avatar
          avatar: [
            {
              id: 1,
              src: 'https://cdn.vuetifyjs.com/images/lists/1.jpg',
            },
            {
              id: 2,
              src: 'https://cdn.vuetifyjs.com/images/lists/2.jpg',
            },
          ],
          heure: '4:00 PM - 5:00 PM',
          titre: 'UI Design',
        },
        {
          id: 3,
          icon: 'mdi-account',
          //groupe d'avatar
          avatar: [
            {
              id: 1,
              src: 'https://cdn.vuetifyjs.com/images/lists/1.jpg',
            },
            {
              id: 2,
              src: 'https://cdn.vuetifyjs.com/images/lists/2.jpg',
            },
            {
              id: 3,
              src: 'https://cdn.vuetifyjs.com/images/lists/3.jpg',
            },
          ],
          heure: '5:00 PM - 6:00 PM',
          titre: 'UX Design',
        },
      ]
    }
  },
}
</script>

<style>
.selected {
  background-color: #000;
}

.selected .text--primary {
  color: #fff;
}
</style>
