<template>
  <div id="app">
    <!-- insert standard header component utilizing slots to populate some data-->
    <mainheader msg="Helping you plan your next wine experience">
      <template v-slot:tagline>Helping you plan your next wine experience</template>
      <template v-slot:WAwine>August 2021 ~ <span class="fst-italic">Join us in celebrating Washington Wine Month!</span> ~ August 2021</template>
    </mainheader>

    <!-- implement nuxt routing for navigation between pages (individual page content in ./src/views)-->
    <div class="bg-danger text-white py-2" id="nav">
      <nuxt-link to="/">Home</nuxt-link> |
      <nuxt-link to="/about">About</nuxt-link> |
      <nuxt-link to="/education">Education</nuxt-link> |
      <nuxt-link to="/news">News</nuxt-link>
    </div>
    <Nuxt />

    <!-- insert standard footer component -->
    <mainfooter msg="test"/>
  </div>
</template>

<script>
// @ is an alias to /src
import mainheader from '@/components/mainheader.vue'
import mainfooter from '@/components/mainfooter.vue'

export default {
  name: 'App',
  components: {
    mainheader,
    mainfooter
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  color: white;
}

#nav a.router-link-exact-active {
  font-weight: bold;
  font-style: italic;
}
</style>
