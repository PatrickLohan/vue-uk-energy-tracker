<template lang="html">
  <h1>rainbows and unicorns</h1>
  <energy-chart :apiData="apiData"></energy-chart>
</template>

<script>

import EnergyChart from '@/components/EnergyChart.vue';

export default {
  name: 'app',
  data(){
    return {
      apiData: {}
    }
  },
  mounted(){
    fetch('https://api.carbonintensity.org.uk/generation')
    .then(res => res.json())
    .then(data => this.apiData = data.data)
  },
  components: {
    'energy-chart': EnergyChart
  }
}
</script>

<style lang="css" scoped>
</style>
