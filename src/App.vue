<template>
  <v-app>
    <v-app-bar
      app
      color="dark"
      dark
    >
      <h1> Tus superheroes favoritos </h1>
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
    superheroes,
  },

  data: () => ({
    //
  }),
};
</script>
