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

<script>

export default {
  data () {
    return {
      // Array will be automatically processed with visualization.arrayToDataTable function
      chartData: [
          ['Country', 'Popularity'],
          ['Germany', 200],
          ['United States', 300],
          ['Brazil', 400],
          ['Canada', 500],
          ['France', 600],
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
