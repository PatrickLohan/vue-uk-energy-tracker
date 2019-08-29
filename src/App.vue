<template lang="html">
  <div>
    <h1>rainbows and unicorns</h1>
    <energy-chart :apiGenerationMix="apiGenerationMix" :apiFrom="apiFrom" :apiTo="apiTo"></energy-chart>
  </div>
</template>

<script>

import EnergyChart from '@/components/EnergyChart.vue';

export default {
  name: 'app',
  data(){
    return {
      apiGenerationMix: [],
      apiFrom:"",
      apiTo:""

    }
  },
  mounted(){
    fetch('https://api.carbonintensity.org.uk/generation')
    .then(res => res.json())
    .then(data => {
      this.apiGenerationMix = data.data.generationmix;
      this.apiFrom = data.data.from;
      this.apiTo = data.data.to;
     });

  },
  components: {
    'energy-chart': EnergyChart
  }
}
</script>

<style lang="css" scoped>
</style>
