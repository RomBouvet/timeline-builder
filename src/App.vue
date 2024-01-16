<script setup>
import CustomTimeline from './components/CustomTimeline.vue'

const events = [
  {
    name: 'Event 1',
    date: 10,
    description: 'Lorem ipsus'
  },
  {
    name: 'Event 2',
    date: 20,
    description: 'Lorem ipsus'
  },
  {
    name: 'Event 0',
    date: -10,
    description: 'Lorem ipsus'
  },
  {
    name: 'Origin',
    date: 0,
    description: 'Lorem ipsus'
  },
]
</script>

<template>
  <div class="wrapper">
    <CustomTimeline :events="events"/>
  </div>
</template>

<style scoped>

</style>
