<template>
  <div class="wrapper">
    <ul class="content">
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
      <li>分类</li>
    </ul>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  data(){
    return {
      scroll : null
    }
  },
  created() {
  
  },
  mounted(){
 this.scroll = new BScroll('.wrapper', {

    })
  }
}
</script>

<style>
.wrapper {
  height: 150px;
  background: red;

  /* overflow-y: scroll; */
}
</style>