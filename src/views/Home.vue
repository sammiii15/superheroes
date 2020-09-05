<template>
  <div class="home">
    <superheroes/>
  </div>
</template>

<script>
// @ is an alias to /src
import superheroes from '@/components/superheroes.vue'
import superhero from '@/components/superhero.vue'

export default {
  name: 'Home',
  components: {
    superheroes,
    superhero
  }
}
</script>

