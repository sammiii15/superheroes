<template>
  <v-container fluid class="my-img" v-id="superhero">
    <v-row justify="center" class="mx-0">
      <v-col cols="12">
        <v-card  dark class="mx-auto my-12" width="350" v-for="superhero in superheroes" :key="superhero.id">
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
            <div class="overline pa-0"> {{superhero.habilidades[0]}} </div>
            <div class="overline pa-0"> {{superhero.habilidades[1]}} </div>
            <div class="overline pa-0"> {{superhero.habilidades[2]}} </div>
            <div class="overline pa-0"> {{superhero.habilidades[3]}} </div>
            <div class="overline pa-0"> {{superhero.habilidades[4]}} </div>
            <div class="overline pa-0"> {{superhero.habilidades[5]}} </div>
            <div class="overline pa-0"> {{superhero.habilidades[6]}} </div>
            <div class="overline pa-0"> {{superhero.habilidades[7]}} </div>
            <div class="overline pa-0"> {{superhero.habilidades[8]}} </div>
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
    name: 'superheroe',

    data: () => ({
      superheroes: [],
      spinfo: '',
    }),
    mounted() {
      this.getSuperHeroes()
      this.getSuperHeroesInfo()
    },
    created() {
      this.getSuperHeroes()
      this.getSuperHeroesInfo()
    },
    methods: {
    getSuperHeroes: function(id) {
      axios
        .get('http://157.245.138.232:9091/api/v1/test/superheroes')
        .then(response => (
          this.superheroes = response.data.data))
        .catch(() => { this.$toast.error('Alerta: error en obtener la información') })
      }
    }   
  }
</script>
<style scoped lang="scss">
  .my-img {
    background-image: url('../assets/img/background.jpg');
    background-repeat: repeat;
    background-size: 90%;
  }

</style>
