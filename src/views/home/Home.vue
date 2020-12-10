<template>
  <div id="home">
    <nav-bar class="home-nav">
      <template #center>
        <div>购物街</div>
      </template>
    </nav-bar>
    <tab-control
      :titles="['流行', '新款', '精选']"
      @tabClick="tabClick"
      ref="tabControl1"
      class="tabControl"
      v-show="isTabFiexd"
    ></tab-control>

    <scroll
      class="content"
      ref="scroll"
      :probe-type="3"
      @scroll="contentScroll"
      :pull-up-load="true"
      @pullingUp="loadMove"
    >
      <recommend-view
        :recommends="recommends"
        @viewImageLoad="viewImageLoad"
      ></recommend-view>
      <feature-view></feature-view>
      <tab-control
        :titles="['流行', '新款', '精选']"
        @tabClick="tabClick"
        ref="tabControl2"
      ></tab-control>
      <goods-list :goods="showGoods"></goods-list>
    </scroll>
  </div>
</template>

<script>
import RecommendView from './childComps/RecommendView'
import FeatureView from './childComps/FeatureView'


import NavBar from 'components/common/navbar/NavBar'
import TabControl from 'components/content/tabControl/TabControl'
import GoodsList from 'components/content/goods/GoodsList'
import Scroll from 'components/common/scroll/Scroll'


import { getHomeMultidate, getHomeGoods } from 'network/home'
import { debounce } from 'common/utils'



export default {
  components: {
    RecommendView,
    FeatureView,

    NavBar,
    TabControl,
    GoodsList,
    Scroll


  },
  data() {
    return {
      banners: [],
      recommends: [],
      goods: {
        'pop': { page: 0, list: [] },
        'new': { page: 0, list: [] },
        'sell': { page: 0, list: [] }
      },
      currentType: 'pop',
      tabbOffsetTop: 0,
      isTabFiexd: false
    }
  },
  computed: {
    showGoods() {
      return this.goods[this.currentType].list
    }
  },
  
  created() {
    this.getHomeMultidate()

    this.getHomeGoods('pop')
    this.getHomeGoods('new')
    this.getHomeGoods('sell')

  },
  mounted() {
    //1图片加载完成事件
    const refresh = debounce(this.$refs.scroll.refresh, 50)

    this.$bus.$on('itemImageLoad', () => {
      refresh()
    })
  },
  methods: {
    // 事件监听
    tabClick(index) {
      switch (index) {
        case 0:
          this.currentType = 'pop'
          break
        case 1:
          this.currentType = 'new'
          break
        case 2:
          this.currentType = 'sell'
          break
      }
      this.$refs.tabControl1.currentIndex =  index
       this.$refs.tabControl2.currentIndex =  index
    },
    backClick() {
      this.$refs.scroll.scrollTo(0, 0)
    },
    contentScroll(position) {
      //1.判断BackTop是否显示
      this.isShowBackTop = (-position.y) > 1000
      //2.决定tabControl是否吸顶
      this.isTabFiexd = (-position.y) > this.tabbOffsetTop
    },
    loadMove() {
      this.getHomeGoods(this.currentType)
    },
    viewImageLoad() {
      this.tabbOffsetTop = this.$refs.tabControl2.$el.offsetTop
      // console.log(this.$refs.tabControl.$el.offsetTop)
    },
    // 网络请求
    getHomeMultidate() {
      getHomeMultidate().then(res => {
        this.banners = res.data.banner.list
        this.recommends = res.data.recommend.list
      })
    },
    getHomeGoods(type) {
      const page = this.goods[type].page + 1
      getHomeGoods(type, page).then(res => {
        this.goods[type].list.push(...res.data.list)
        this.goods[type].page += 1

        this.$refs.scroll.finishPullUp()
      })
    }

  }
}
</script>

<style scoped>
#home {
  padding-top: 44px;
  height: 100vh;
  position: relative;
}
.home-nav {
  background: var(--color-tint);
  color: white;

  position: fixed;
  top: 0;
  left: 0;
  right: 0;

  z-index: 100;
}

.content {
  position: absolute;
  /* height: 300px; */
  top: 44px;
  bottom: 49px;
}
.tabControl {
  position: relative;
  z-index: 9;
}
</style>