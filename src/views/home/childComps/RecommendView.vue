<template>
  <div class="recommend">
    <div v-for="item in recommends" :key="item.num" class="recommend-item">
      <a :href="item.link">
        <img :src="item.image" alt="" @load="imageLoad" />
        <div>{{ item.title }}</div>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    recommends: {
      type: Array,
      default() {
        return []
      }
    }
  },
  data() {
    return {
      isLoad: false
    }
  },
  methods: {
    imageLoad() {
      if (!this.isLoad) {
        this.$emit('viewImageLoad')
        this.isLoad = true
      }

    }
  }


}
</script>

<style>
.recommend {
  display: flex;
  text-align: center;
  padding: 15px 0 30px;
  border-bottom: 8px solid #eee;
}
.recommend-item {
  flex: 1;
}
.recommend-item img {
  width: 65px;
  height: 65px;
}
</style>