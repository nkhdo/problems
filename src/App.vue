<template>
  <div id="app">
    <top-navbar/>
    <div class="container mt-4 mb-4">
      <router-view/>
    </div>
  </div>
</template>

<script>
import TopNavbar from '@/components/TopNavbar'

export default {
  name: 'App',
  components: {
    TopNavbar
  }
}
</script>

<style lang="scss"> </style>
