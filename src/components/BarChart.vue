<template>
  <div>
    <canvas id="barChart"></canvas>
  </div>
</template>

<script>
import axios from "axios";
import Chart from "chart.js";

import barChartData from "../bar-data.js";

export default {
  name: "BarChart",
  data() {
    return {
      barChartData: barChartData,
    };
  },
  async mounted() {
    const ctx = document.getElementById("barChart");

    await axios.get("https://covid19.mathdro.id/api/countries/BRA").then(
      (response) => {
        // console.log(parseInt(response.data["confirmed"].value));

        this.barChartData.data.datasets[0].data[0] =
          response.data["confirmed"].value;

        this.barChartData.data.datasets[0].data[1] =
          response.data["recovered"].value;

        this.barChartData.data.datasets[0].data[2] =
          response.data["deaths"].value;
      },
      (error) => {
        console.log("error", error);
      }
    );

    new Chart(ctx, this.barChartData);
  },
};
</script>
