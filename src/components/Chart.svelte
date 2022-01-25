<script>
  import { afterUpdate } from "svelte";
  import Highcharts from "highcharts";
  import data from "../data/chart.json";

  export let age = 16;

  afterUpdate(() => {
    Highcharts.chart("container", {
      chart: {
        plotBackgroundColor: null,
        plotBorderWidth: 0,
        style: {
          fontFamily: "sans-serif",
        },
      },
      title: {
        text: "",
      },
      credits: {
        enabled: false,
      },
      xAxis: {
        categories: [2015, 2016, 2017, 2018, 2019, 2020, 2021],
      },
      yAxis: {
        title: "",
        labels: {
          format: "{value}%",
        },
      },
      plotOptions: {
        series: {
          events: {
            legendItemClick: function () {
              return false;
            },
          },
        },
      },
      legend: {
        itemStyle: {
          cursor: "default",
        },
        enabled: !0,
        borderWidth: 1,
        borderRadius: 2,
        margin: 30,
        padding: 15,
      },
      tooltip: {
        style: {
          fontSize: "8pt",
        },
        formatter: function () {
          return (
            '<div class="hc-tooltip"><span class="label">' +
            this.key +
            '</span><br/><span class="data" style="color:' +
            this.point.series.color +
            '">' +
            this.point.series.name +
            " </span><span><b>" +
            this.y.toFixed(1) +
            "%</b><span></div>"
          );
        },
      },
      series: [
        {
          type: "column",
          name: "Past: 1-year return",
          color: "#5EB9E4",
          legendIndex: 1,
          data: data[age].oneYearReturn,
        },
        {
          type: "line",
          name: "Average Return",
          color: "#6E267B",
          legendIndex: 2,
          data: data[age].averageReturn,
        },
        {
          type: "line",
          name: "Average Return Target",
          color: "#FF7F50",
          legendIndex: 3,
          data: data[age].averageReturnTarget,
        },
      ],
    });
  });
</script>

<div id="container" />

<style>
  div {
    width: 100%;
    height: 500px;
    margin-bottom: 20px;
  }
</style>
