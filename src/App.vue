<template>
  <div id="app">
    <cx-header :seller="seller"/>
  </div>
</template>

<script>
import CxHeader from 'components/cx-header/cx-header'

import { getSeller } from 'api'

export default {
  data() {
    return {
      seller: {}
    }
  },
  components: {
    CxHeader
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
</style>
