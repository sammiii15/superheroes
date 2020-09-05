<template>
  <v-container fluid class="my-img">
    <v-row justify="center" class="mx-0">
      <v-col cols="12" sm="12" md="3" lg="2" v-for="superhero in superheroes" :key="superhero.id">
        <v-card  dark class="mx-auto my-12" width="350" >
          <v-img align-self="start" @click="goTosuperhero(superhero)"
                 class="fill-width" height="350px" transition="scale-transition" :src="superhero.avatarURL"/>
          <v-card-title align="center" class="headline mb-1">
            {{superhero.nombre}}
          </v-card-title>
          <v-card-subtitle>
            {{superhero.nombreReal}}
            <div class="subtitle-2" v-if="superhero.puedeVolar === true"> Puede volar </div>
          </v-card-subtitle>
          <v-card-actions light justify="center" class="headline mb-1">
            <v-btn color="red lighten-2" @click="goTosuperhero(superhero)">
              Ver más
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
    <v-row  justify="center" class="mx-0">
      <v-col cols="8">
        <v-card class="mx-auto my-12 pa-2" align="center">
          <h1> Quieres saber quienes de estos superhéroes pueden volar?😱😱😱 </h1>
          <v-dialog v-model="dialog" width="500" class="subtitle-2">
          <template v-slot:activator="{ attrs }">
            <v-btn color="red lighten-2"  dark v-bind="attrs" @click="dialog = true">
              Sii quiero saber!😄
            </v-btn>
          </template>
          <v-card>
            <div v-for="superhero in superheroes" :key="superhero.id">
              <v-card-title class="headline grey lighten-2" v-if="superhero.puedeVolar === true" >
                {{superhero.nombre}}
              </v-card-title>
            </div>
            <v-divider></v-divider>
            <v-card-actions align="center">
            <v-spacer></v-spacer>
            <v-btn
            color="primary"
            text
            @click="dialog = false">
              Genial!! 😄
            </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  import axios from "axios";

  export default {
    name: 'superheroes',

    data: () => ({
      superheroes: [],
      dialog: false
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
        .catch(() => { this.$toast.error('Alerta: error en obtener la información') })
      },
      goTosuperhero: function(superhero) {
        this.$router.push({name:'superhero', params: { id:superhero.id }})
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
