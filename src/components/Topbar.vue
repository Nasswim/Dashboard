<template>
  <v-app-bar class="mx-8 mt-10" color="white" flat>
    <v-container>
      <v-row>
        <v-col cols="6">
          <div align="center" class="d-flex justify-space-between">
            <h1 class="ml-9" style="font-size: 40px">Schedule</h1>
            <div align="center" style="align-items: center; display: flex; margin-right: 110px">
              <span class="mr-2 font-weight-bold" style="font-size: 18px"
                >Aug 5, 2021</span
              >
              <v-icon color="black">mdi-menu-down-outline</v-icon>
            </div>
          </div>
        </v-col>
        <v-col cols="6">
          <div class="ml-8 d-flex justify-space-between">
            <v-text-field
              class="mr-5"
              color="black"
              prepend-inner-icon="mdi-magnify"
              value="Search"
              solo-inverted
            ></v-text-field>
            <v-avatar>
              <img
                src="../assets/logo-avatar-orange.png"
                alt="image d'un avatar orange"
              />
            </v-avatar>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </v-app-bar>
</template>
