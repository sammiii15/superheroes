<template>
  <v-app  style="background: rgba(0,0,0,0);">
    <v-app-bar
      app
      color="primary"
      dark
    >
    </v-app-bar>

    <v-main>
      <superheroes/>
    </v-main>
  </v-app>
</template>

<script>
import superheroes from './components/superheroes';

export default {
  name: 'App',

  components: {
    superheroes
  },

  data: () => ({
    //
  }),
};
</script>
