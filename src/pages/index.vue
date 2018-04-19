<template>
  <section class="container">
      <coin-table :data="mockData"></coin-table>
  </section>
</template>


<script>
import CoinTable from '../components/CoinTable'
import axios from 'axios'

export default {
    async asyncData() {
        let {data} = await axios.get('')
        return {realData: data}        
    },
    data: () => ({
        mockData: [
            {
                name: 'BTC',
                price: 200000,
                marketGap: 200000,
                currency: '$',
                id: 0
            },
            {
                name: 'USDT',
                price: 600000,
                marketGap: 200000,
                currency: '$',
                id: 1
            },
            {
                name: 'ETH',
                price: 300000,
                marketGap: 200000,
                currency: '$',
                id: 2
            },
            {
                name: 'ETC',
                price: 200000,
                marketGap: 200000,
                currency: '$',
                id: 3
            }
        ]
    }),
    components: {CoinTable}
}
</script>



<style>

</style>
