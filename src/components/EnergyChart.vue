<template>
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
          subtitle: '% of total'
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
      let sortedArray = energyArray.sort(function(a, b) { return b[1] - a[1]; });
      return sortedArray;
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
