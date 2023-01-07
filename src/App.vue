<template>
  <v-app>
    <Sidebar />

    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue';
import Sidebar from '@/components/Sidebar.vue';

export default Vue.extend({
  name: 'App',
  components: { Sidebar },

  data: () => ({
    //
  }),
});
</script>

<style>
  
</style>
