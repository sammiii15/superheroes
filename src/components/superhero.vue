<template>
  <v-container fluid class="my-img" v-if="superhero">
    <v-row justify="center" class="mx-0">
      <v-col cols="12">
        <h1> hola </h1>
        <v-card  dark class="mx-auto my-12" width="350">
          <v-img align-self="start" class="fill-width" height="350px" transition="scale-transition" :src="superhero.avatarURL"/>
          <v-card-title align="center" class="headline mb-1">
            {{superhero.nombre}}
          </v-card-title>
          <v-card-subtitle>
            {{superhero.nombreReal}}
            <div class="subtitle-2" v-if="superhero.puedeVolar === true"> Puede volar </div>
          </v-card-subtitle>
          <v-card-text class="my-4 subtitle-1" align="center" justify="center">
            {{ superhero.descripcion }}
          </v-card-text>
          <v-list-content align="center">
            <div class="overline pb-1"> Habilidades </div>
            <div class="overline pa-0"> {{superhero.habilidades}} </div>
            <div class="overline pa-0"> {{superhero.habilidades}} </div>
            <div class="overline pa-0"> {{superhero.habilidades}} </div>
            <div class="overline pa-0"> {{superhero.habilidades}} </div>
            <div class="overline pa-0"> {{superhero.habilidades}} </div>
            <div class="overline pa-0"> {{superhero.habilidades}} </div>
            <div class="overline pa-0"> {{superhero.habilidades}} </div>
            <div class="overline pa-0"> {{superhero.habilidades}} </div>
            <div class="overline pa-0"> {{superhero.habilidades}} </div>
          </v-list-content>
          <v-card-actions light justify="center" class="headline mb-1">
            <v-btn v-if="superhero.puedeVolar === true"> Ver más </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  import axios from "axios";


  export default {
    name: 'superhero',
    props: ['superhero.id'],
    data: () => ({
      superhero: null
    }),
    mounted() {
      const { id } = this.$route.params
      if (id) {
        this.getSuperHeroe(id)
      } 
    },
    watch: {
      '$route' () {
        const { id } = this.$route.params
        if (id) {
          this.getSuperHeroe(id)
        }
      } 
    },
    methods: {
    getSuperHeroe: function(id) {
      axios
        .get('http://157.245.138.232:9091/api/v1/test/superheroes/?id')
        .then(response => (
          this.superhero = response.data.data))
        .catch(error => {
        this.errorMessage = error.message;
        console.error("There was an error!", error);
      })
    }   
    }
  }
</script>