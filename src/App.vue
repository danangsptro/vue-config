<template>
  <div>
    <div id="nav">
      <!-- <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> -->
      <Nav />
    </div>
    <router-view />
  </div>
</template>

<script lang="js">
import Nav from '@/layouts/nav.vue'
export default {
  components:{
    Nav,
  }
}
</script>
