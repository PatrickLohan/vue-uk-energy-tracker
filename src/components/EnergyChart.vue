<template lang="html">
  <GChart
    type="ColumnChart"
    :data="chartData"
    :options="chartOptions"
    />
</template>

<script>
import { GChart } from 'vue-google-charts'

export default {
  name: 'energy-chart',
  data(){
    return {
      // chartData: this.getData,
      chartOptions: {
        chart: {
          title: 'UK Energy Use By Fuel',
          // subtitle: 'Dank memes'
          subtitle: this.apiData.from
        }
      }
    }
  },
  computed: {
    chartData: function(){
      // return this.apiData.generationmix.forEach((object) => {
        // return object
      // })
      const energyArray = [['Fuel', 'Percentage']]
      for (let object of this.apiData.generationmix){
        energyArray.push([object.fuel, object.perc])
      }
      return energyArray;
    },
  },
  props: ['apiData'],
  components: {
    GChart
  }
}
</script>

<style lang="css" scoped>
</style>
