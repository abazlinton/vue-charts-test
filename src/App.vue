<template>
  <section>
    <button @click="addRussia">Add Russia</button>
    <GChart
      type="GeoChart"
      
      :data="chartData"
      :options="chartOptions"
      :events="chartEvents"
      ref="gChart"
    />  
  </section>
</template>

// :settings="{ packages: ['corechart', 'table'], mapsApiKey: 'key here' }"

<script>

export default {
  data () {
    return {
      // Array will be automatically processed with visualization.arrayToDataTable function
      chartData: [
          ['Country', 'Popularity'],
      ],
      chartOptions: {
        chart: {
          
        }
      },
      chartEvents: {
         select: () => {          
          const blah = this.$refs.gChart.chartObject;
          console.log(this.chartData, blah.getSelection())
        }
      }
    }
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
      .then(response => response.json())
      .then(countries => this.chartData = this.chartData.concat(countries.map(country => [country.alpha2Code, country.population])))
  },
  methods: {
    addRussia(){
      this.chartData.push(['Russia', 600])
    },
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
