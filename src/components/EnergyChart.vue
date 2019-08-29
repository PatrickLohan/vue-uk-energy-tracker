<template lang="html">
  <div id="chartShown">
  <GChart
    type="ColumnChart"
    :data="chartData"
    :options="chartOptions"
    />
  </div>
</template>

<script>
import { GChart } from 'vue-google-charts'

export default {
  name: 'energy-chart',
  data(){
    return {
      chartOptions: {
        chart: {
          title: 'UK Energy Use By Fuel',
          subtitle: 'Dank memes'
        }
      }
    }
  },
  computed: {
    chartData: function(){
      const energyArray = [['Fuel', 'Percentage']]
      for (let object of this.apiGenerationMix){
        energyArray.push([object.fuel, object.perc])
      }
      return energyArray;
    },
  },
  mounted(){
  },
  props: ['apiGenerationMix', 'apiFrom', 'apiTo'],
  components: {
    GChart
  }
}
</script>

<style lang="css" scoped>
</style>
