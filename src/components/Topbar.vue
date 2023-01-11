<template>
  <v-app-bar class="ma-8" color="white" flat>
    <v-row class="justify-space-between">
      <h1 class="ma-9 ">Schedule</h1>
    </v-row>
    <v-row class="ml-15 mb-2">
      <span class="caption mr-2">Aug 5, 2021</span>
      <v-icon color="black">mdi-menu-down-outline</v-icon>
    </v-row>
    <v-row>
      <v-text-field
        class="mr-5"
        color="black"
        prepend-inner-icon="mdi-magnify"
        value="Search"
        solo-inverted
      ></v-text-field>
      <v-avatar>
        <img
          src="https://i.pinimg.com/originals/6c/85/40/6c85408b15e4cd7168c2de9c34d9384d.jpg"
          alt="CR7"
        />
      </v-avatar>
    </v-row>
  </v-app-bar>
</template>
