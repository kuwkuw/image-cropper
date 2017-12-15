<template>
  <span :class="position" class="pin" @mousedown="onMousedown"></span>
</template>

<script>
  export default {
    name: 'pin',
    props: ['position'],
    methods: {
      onMousedown (event) {
        this.$emit('mousedown', event)
      }
    }
  }
</script>

<style>
  .left-top{
    top: -10px;
    left: -10px;
  }
  .right-top{
    top: -10px;
    right: -10px;
  }
  .left-bottom{
    bottom: -10px;
    left: -10px;
  }
  .right-bottom{
    bottom: -10px;
    right: -10px;
  }
  .pin {
    background: #000;
    position: absolute;
    z-index: 1001;
    width: 20px;
    height: 20px;
    display: block;
    border-radius: 20px;
  }
</style>
