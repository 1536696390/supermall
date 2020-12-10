<template>
  <div id="detail">
    <detail-nav-bar />
    <scroll class="content">
      <detail-swiper :top-images="topImages" />
      <detail-base-info :goods="goods" />
      <detail-shop-info :shop="shop" />
    </scroll>
  </div>
</template>

<script>
import DetailNavBar from './childConmps/DetailNavBar'
import DetailSwiper from './childConmps/DetailSwiper'
import DetailBaseInfo from './childConmps/DetailBaseInfo'
import DetailShopInfo from './childConmps/DetailShopInfo'

import Scroll from 'components/common/scroll/Scroll'
import { getDetail, Goods, Shop } from 'network/detail'
export default {
  name: 'Detail',
  components: {
    DetailNavBar,
    DetailSwiper,
    DetailBaseInfo,
    DetailShopInfo,
    Scroll
  },
  data() {
    return {
      iid: null,
      topImages: [],
      goods: {},
      shop: {},
    }
  },
  
  created() {
    this.iid = this.$route.params.iid
    // console.log(this.$route.params)
    getDetail(this.iid).then(res => {
      console.log(res)
      const data = res.result
      this.topImages = data.itemInfo.topImages
      //2获取商品信息
      console.log(this.goods = new Goods(data.itemInfo, data.columns, data.shopInfo.services))
      this.goods = new Goods(data.itemInfo, data.columns, data.shopInfo.services)
      //3.创建店铺的信息

      this.shop = new Shop(data.shopInfo)
      console.log(this.shop)
 
    })
  }
}
</script>

<style scoped>
#detail {
  position: relative;
  z-index: 9;
  background-color: #fff;
  height: 100vh;
}
.content {
  height: calc(100% - 44px);
}
</style>
