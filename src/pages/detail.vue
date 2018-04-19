<template>
  <div class="detail-container">
      <top-banner :data="mockData"></top-banner>

      <div class="chart-container">
          <ve-line :data="chartData" :settings="chartSettings"></ve-line>
      </div>
  </div>

</template>


<script>
import TopBanner from '../components/TopBanner'
import axios from 'axios'
import VeLine from 'v-charts/lib/line'

export default {
    name: 'detail-container',
    data: () => ({
        mockData: {
            name: 'BTC',
            price: 200000,
            marketGap: 200000,
            currency: '$',
            id: 0
        }
    }),
    // this.$router.params.coinId 
    async asyncData () {
      let {data} = await axios.get('')
      return { realData: data }  
    },
    components: {
        TopBanner, VeLine
    },
    created () {
        this.chartData = {
        columns: ['日期', '成本', '利润', '占比', '其他'],
        rows: [
          { '成本': 1523, '日期': '1月1日', '利润': 1523, '占比': 0.12, '其他': 100 },
          { '成本': 1223, '日期': '1月2日', '利润': 1523, '占比': 0.345, '其他': 100 },
          { '成本': 2123, '日期': '1月3日', '利润': 1523, '占比': 0.7, '其他': 100 },
          { '成本': 4123, '日期': '1月4日', '利润': 1523, '占比': 0.31, '其他': 100 },
          { '成本': 3123, '日期': '1月5日', '利润': 1523, '占比': 0.12, '其他': 100 },
          { '成本': 7123, '日期': '1月6日', '利润': 1523, '占比': 0.65, '其他': 100 }
        ]
      }
      this.chartSettings = {
        metrics: ['成本', '利润'],
        dimension: ['日期']
      }
    }

}
</script>



<style>

</style>
