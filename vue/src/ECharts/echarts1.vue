<template>
  <div style="width: auto;height: 470px" id="echarts1">
  </div>
</template>

<script>
import echarts from 'echarts'
const colors = ['#5470C6', '#EE6666']
export default {
  name: 'echarts1',
  data () {
    return {
      // option配置
      option: {
        color: colors,
        tooltip: {
          trigger: 'none',
          axisPointer: {
            type: 'cross'
          }
        },
        legend: {},
        grid: {
          top: 70,
          bottom: 50
        },
        xAxis: [
          {
            type: 'category',
            axisTick: {
              alignWithLabel: true
            },
            axisLine: {
              onZero: false,
              lineStyle: {
                color: colors[0]
              }
            },
            axisPointer: {
              label: {
                formatter: function (params) {
                  return (
                      '工厂异常事件发生频率  ' +
                      params.value +
                      (params.seriesData.length ? '：' + params.seriesData[0].data : '')
                  )
                }
              }
            },
            // prettier-ignore
            data: ['2022-1', '2022-2', '2022-3', '2022-4', '2022-5', '2022-6', '2022-7', '2022-8', '2022-9', '2022-10', '2022-11', '2022-12']
          },
          {
            type: 'category',
            axisTick: {
              alignWithLabel: true
            },
            axisLine: {
              onZero: false,
              lineStyle: {
                color: colors[1]
              }
            },
            axisPointer: {
              label: {
                formatter: function (params) {
                  return (
                      '机器故障发生频率  ' +
                      params.value +
                      (params.seriesData.length ? '：' + params.seriesData[0].data : '')
                  )
                }
              }
            },
            // prettier-ignore
            data: ['2022-1', '2022-2', '2022-3', '2022-4', '2022-5', '2022-6', '2022-7', '2022-8', '2022-9', '2022-10', '2022-11', '2022-12']
          }
        ],
        yAxis: [
          {
            type: 'value'
          }
        ],
        series: [
          {
            name: '工厂异常事件发生频率(2023)',
            type: 'line',
            xAxisIndex: 1,
            smooth: true,
            emphasis: {
              focus: 'series'
            },
            data: [
              2.6, 5.9, 9.0, 26.4, 28.7, 70.7, 175.6, 182.2, 48.7, 18.8, 6.0, 2.3
            ]
          },
          {
            name: '机器故障发生频率(2023)',
            type: 'line',
            smooth: true,
            emphasis: {
              focus: 'series'
            },
            data: [
              3.9, 5.9, 11.1, 18.7, 48.3, 69.2, 231.6, 46.6, 55.4, 18.4, 10.3, 0.7
            ]
          }
        ]
      }
    }
  },
  mounted () {
    this.echartsInit()
  },
  methods: {
    echartsInit () {
      // 在生命周期中挂载
      echarts.init(document.getElementById('echarts1')).setOption(this.option)
    }
  }
}
</script>

<style scoped>

</style>