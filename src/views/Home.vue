<template>
  <div class="home">
    
    <the-home/>
    <img alt="Vue logo" src="../assets/logo.png">
  </div>
</template>

<script>
// @ is an alias to /src


import TheHome from '../components/TheHome.vue'

export default {
  name:'Home',
  components: {
    TheHome
  }
}
</script>
