<template>
  <v-app>
    <Navbar/>
    <v-content>
      <Home/>
      <router-view></router-view>
    </v-content>
  </v-app>
</template>

<script>
import Navbar from '../src/components/Navbar'
import Home from '../src/views/Home'
export default {
  name: 'App',

  components: {
    Navbar,
    Home
  },

  data: () => ({
    //
  }),
};
</script>
