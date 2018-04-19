<template>
  <div class="coin-list-item-container" @click="itemClick(data.id)">
      <div class="item-small index">{{index}}</div>
      <div class="item coin">
        <name-image-holder :imageSrc="data.name"></name-image-holder>
      </div>

      <div class="item price">
        <currency-holder :currency="data.currency" :total="data.price" />
      </div>
      <div class="item market-gap">
         <currency-holder :currency="data.currency" :total="data.marketGap" />
      </div>
  </div>
</template>

<script>
import CurrencyHolder from './CurrencyHolder'
import NameImageHolder from './NameImageHolder'
var self = this;

export default {
  components: {
    CurrencyHolder, NameImageHolder
  },
  name: 'coin-list-item',
  data: () => ({

  }),
  methods: {
    itemClick(id) {
      this.$router.push({
        name: 'DetailPage',
        params: {
          coinId: id
        }
      })
    }
  },
  props: ['index', 'data']
}

</script>


<style>
.coin-list-item-container {
  min-width: 1000px;
  position: relative;
  overflow: hidden;
  height: 40px;
  line-height: 40px;
  cursor: pointer;
}

.coin-list-item-container .item {
  position: relative;
  float: left;
  width: 30%;
}

.coin-list-item-container .item-small {
  position: relative;
  float: left;
  width: 10%;
}

</style>
