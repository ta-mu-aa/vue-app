
<script>
import { Bar } from 'vue-chartjs';

export default {
  name: 'Chart',
  extends: Bar,
  data () {
    return {
      data: {
        labels: ['胸', '肩', '腕', '背中', '脚', '腹'],
        datasets: [
          { 
            data: [],
            backgroundColor: [
              'rgba(255, 99, 132, 0.5)',
              'rgba(255, 159, 64, 0.5)',
              'rgba(100, 192, 192, 0.5)',
              'rgba(54, 162, 235, 0.5)',
              'rgba(0, 0, 0, 0.5)',
              'rgba(203, 202, 50, 0.5)',
            ],
            borderColor: [
              'red',
              'orange',
              'green',
              'blue',
              'black',
              'yellow'
            ],
            borderWidth: 1
          },
        ]
      },
      options: {
        legend: {
          display: false
        },
        scales: {
          xAxes: [{
            scaleLabel: {
              display: true,
              labelString: 'week'
            }
          }],
          yAxes: [{
            ticks: {
              beginAtZero: true,
              stepSize: 5,
            }
          }]
        }
      }
    }
  },
  mounted () {
    this.renderChart(this.data, this.options)
    console.log(this.$store.state.trainingMenu)
  }
}
</script>
