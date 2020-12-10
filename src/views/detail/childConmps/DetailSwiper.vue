<template>

    <swiper  class="detail-swiper">
      <swiper-item v-for="item in topImages" :key="item.a">
        <img :src="item" alt="">
      </swiper-item>
    </swiper>

</template>

<script>
import { Swiper, SwiperItem } from 'components/common/swiper'

export default {
  name: '',
  components: {
    Swiper,
    SwiperItem
  },
  data() {
    return {}
  },
  props: {
    topImages: {
      type: Array,
      default() {
        return []
      }
    }
  }
}
</script>

<style scoped>
.detail-swiper{
  height: 300px;
  overflow: hidden;
}
.detail-swiper img{

  height: 451px;
}
</style>
