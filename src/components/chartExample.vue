<template>
  <div class="container">
    <div class="row">
      <div class="col-sm">
        <h1> Vue.js Data Visualization</h1>
        <p>In which we examine creating a component for Vue in the form of a chart.</p>
      </div>
    </div>

    <div class="row">
      <div class="form-group col-4">
        <div v-for="(t, index) in sales">
          <label> {{sales[index].month}} 
            <input v-model.number="sales[index].total" type="number" >
          </label>
        </div>
      </div>
      <div class="col">
        <div class="row">
          <div class="col-6">
            <v-chart v-bind:chartData="lineGraphData"></v-chart>
          </div>
          <div class="col-6">
            <v-chart v-bind:chartData="barChartData"></v-chart>
          </div>
        </div>
        <div class="row">
          <div class="col-6">
            <v-chart v-bind:chartData="vBarChartData"></v-chart>
          </div>
        </div>  
      </div>
    </div>
  </div>
</template>

<script>
import sales from "../assets/data/sales";

export default {
  name: "barChartExample",
  data() {
    return {
      sales: sales,
      barChartData: {
        chartType: "pieChart",
        selector: "chart",
        title: "Sales by Month",
        width: 300,
        height: 200,
        metric: "total",
        dim: "month",
        data: sales
      },
      lineGraphData: {
        chartType: "scatterPlot",
        selector: "graph",
        title: "Sales by Month",
        width: 300,
        height: 200,
        metric: "total",
        dim: "month",
        data: sales
      },
      vBarChartData: {
        chartType: "vBarChart",
        selector: "vChart",
        title: "Sales by Month",
        width: 300,
        height: 200,
        metric: "total",
        dim: "month",
        data: sales
      }
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.chart-barChart {
  fill: blue;
}

.chart-barChart:hover {
  fill: #37386b;
}

.chart-vBarChart {
  fill: red;
}
</style>
