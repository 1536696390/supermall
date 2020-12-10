<template>
  <div id="tab-bar">
    <slot></slot>
  </div>
</template>

<script>
export default {

}
</script>

<style>
#tab-bar {
  display: flex;
  text-align: center;
  background: #f6f6f6;
  position: fixed;
  left: 0;
  right: 0;
  bottom: -1px;
  box-shadow: 0px -3px 1px rgba(100, 100, 100, 0.2);
}

</style>