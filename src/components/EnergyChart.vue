<template lang="html">
  <GChart
    type="ColumnChart"
    :data="chartData"
    :options="chartOptions"
</template>

<script>
import { GChart } from 'vue-google-charts'

export default {
  name: 'energy-chart',
  data(){
    return {
      chartData: [],
      chartOptions: {}
    }
  }
  components: {
    GChart
  }
}
</script>

<style lang="css" scoped>
</style>
