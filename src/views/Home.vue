<template>
  <div class="home">
    <superheroes msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import superheroes from '@/components/superheroes.vue'

export default {
  name: 'Home',
  components: {
    superheroes
  }
}
</script>

