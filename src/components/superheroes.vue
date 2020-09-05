<template>
  <v-container fluid>
    <v-row class="text-center">
      <v-col cols="12">
        <v-card  dark class="mx-auto my-12" width="400" v-for="superhero in superheroes" :key="superhero.id">
          <v-img align-self="start" class="fill-width" height="400px" transition="scale-transition" aspect-ratio="2" :src="superhero.avatarURL"/>
          <h1> {{ superhero.nombre }} </h1>
          <v-card-title>
            {{superhero.nombre}}
          </v-card-title>
          <v-card-subtitle>
            {{ superhero.puedeVolar }}
          </v-card-subtitle>
          <v-card-text v-if="superhero.puedeVolar === true ">
            {{superhero.nombreReal}}
          </v-card-text>
          <v-list-content  v-if="superhero.puedeVolar === true" >
            <div class="headline mb-1"> Habilidades </div>
            <div class="overline mb-4"> {{superhero.habilidades[0]}} </div>
            <div class="overline mb-4"> {{superhero.habilidades[1]}} </div>
            <div class="overline mb-4"> {{superhero.habilidades[2]}} </div>
            <div class="overline mb-4"> {{superhero.habilidades[3]}} </div>
            <div class="overline mb-4"> {{superhero.habilidades[4]}} </div>
            <div class="overline mb-4"> {{superhero.habilidades[5]}} </div>
            <div class="overline mb-4"> {{superhero.habilidades[6]}} </div>
            <div class="overline mb-4"> {{superhero.habilidades[7]}} </div>
            <div class="overline mb-4"> {{superhero.habilidades[8]}} </div>
          </v-list-content>
        </v-card>
        <v-img
          :src="require('../assets/logo.svg')"
          class="my-3"
          contain
          height="200"
        />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  import axios from "axios";

  export default {
    name: 'superheroes',

    data: () => ({
      superheroes: []
    }),
    mounted() {
      this.getSuperHeroes()
    },
    created() {
      this.getSuperHeroes()
    },
    methods: {
    getSuperHeroes: function() {
      axios
        .get('http://157.245.138.232:9091/api/v1/test/superheroes')
        .then(response => (
          this.superheroes = response.data.data))
        .catch(error => console.log(error))
      }
    }   
  }
</script>
<style scoped lang="scss">
  .my-img {
    display: flex;
    vertical-align: top;
  }

</style>
