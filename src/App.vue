<template>
  <div id="app">
    <cx-header :seller="seller"/>
    <div class="tab-wrapper">
      <tab :tabsList="tabsList" :initialIndex="0"/>
    </div>
  </div>
</template>

<script>
import CxHeader from 'components/cx-header/cx-header'
import Tab from 'components/tab/tab'
import Goods from 'components/goods/goods'
import Ratings from 'components/ratings/ratings'
import Seller from 'components/seller/seller'
import { getSeller } from 'api'

export default {
  data() {
    return {
      seller: {}
    }
  },
  computed: {
    tabsList() {
      return [
        {
          label: "商品",
          component: Goods,
          data: this.seller
        },
        {
          label: "评价",
          component: Ratings,
          data: this.seller
        },
        {
          label: "商品2",
          component: Seller,
          data: this.seller
        },
      ]
    }
  },
  components: {
    CxHeader,
    Tab,
    Goods,
    Ratings,
    Seller
  },
  created() {
    this.init()
  },
  methods: {
    init() {
      getSeller().then(res => {
        this.seller = res;
      })
    } 
  }
}
</script>

<style lang="stylus" scoped>
  .tab-wrapper
    position fixed
    top 136px
    left 0
    right 0
    bottom 0
</style>
