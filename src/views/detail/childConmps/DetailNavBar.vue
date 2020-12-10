<template>
  <div>
    <nav-bar>
      <!-- <template #center>
        <div v-for="item in titles" :key="item.titles" class="title">
          <div class="title-item">{{ item }}</div>
        </div>
      </template> -->
      <div slot="center" class="title">
        <div
          v-for="(item, index) in titles"
          :key="item.titles"
          class="title-item" :class="{active : index === currentIndex}"
          @click="titleClick(index)"
        >
          {{ item }}
        </div>
      </div>
      <div slot="left" @click="backClick">
        <img src="~assets/img/common/back.svg" alt="" >
      </div>
    </nav-bar>
  </div>
</template>

<script>
import NavBar from 'components/common/navbar/NavBar'
export default {
  name: '',
  components: {
    NavBar
  },
  data() {
    return {
      titles: ['商品', '参数', '评论', '推荐'],
      currentIndex: 0
    }
  },
  methods:{
    titleClick(index){
      this.currentIndex = index
    },
    backClick(){
     this.$router.back()
    }
  }

}
</script>

<style scoped>
.title {
  display: flex;
  font-size: 13px;
}
.title-item {
  flex: 1;
}
.active{
  color: var(--color-tint);
}
</style>
