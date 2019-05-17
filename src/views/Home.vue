<template>
  <div>
    <div v-for="problem in problems" :key="problem.name">
      <router-link :to="problem.link">
        {{ problem.name }}
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      problems: [
        {
          name: 'Problem 1',
          link: '/problem-1'
        }
      ]
    }
  }
}
</script>
