<template>
  <div class="grafico">
    <pie-chart :data="chartData" :options="chartOptions"></pie-chart>
  </div>
</template>

<script>
import PieChart from "./../PieChart.js";
export default {
  name: "Grafico01",
  components: {
    PieChart
  },
  props:[
      "cores",
      "numeros"
  ],
  data() {
    return {
      chartOptions: {
        hoverBorderWidth: 20
      },
      chartData: {
        hoverBackgroundColor: "red",
        hoverBorderWidth: 10,
        labels: ["Proteinas", "Carboidratos", "Gorduras", "Água"],
        datasets: [
          {
            label: "Data One",
            backgroundColor: this.cores,
            data: this.numeros
          }
        ]
      }
    };
  }
};
</script>

<style scoped>
.grafico {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  width: 40%;
  height: 40%;
}

</style>
