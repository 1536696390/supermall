<template>
  <div id="home">
    <nav-bar class="home-nav">
      <template #center>
        <div>购物街</div>
      </template>
    </nav-bar>
   <recommend-view :recommends="recommends"></recommend-view>
  </div>
</template>

<script>
import NavBar from 'components/common/navbar/NavBar'
import RecommendView from './childComps/RecommendView'


import { getHomeMultidate } from 'network/home'



export default {
  components: {
    NavBar,
 
    RecommendView
    
   
  },
  data() {
    return {
      banners: [],
      recommends: []
    }
  },
  created() {
    getHomeMultidate().then(res => {
      this.banners = res.data.banner.list
      this.recommends = res.data.recommend.list
      console.log(res)
    })
  }
}
</script>

<style>
.home-nav {
  background: var(--color-tint);
  color: white;
}
</style>