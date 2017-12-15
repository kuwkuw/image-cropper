<template>
  <div
    v-if="cropBoxData"
    class="croped-img-container"
    :style="{left: cropBoxData.left + 'px', top: cropBoxData.top + 'px'}"
    @dblclick="onDblclick"
    @mousemove="handleMousMovment">
    <img
      :style="{width: cropBoxData.width + 'px', height: cropBoxData.height +'px'}"
      :src="cropImg">
    <pin
      :position="'left-top'"
      @mousedown="startSelect" />
    <pin
      :position="'right-top'"
      @mousedown="startSelect"/>
    <pin
      :position="'left-bottom'"
      @mousedown="startSelect"/>
    <pin
      :position="'right-bottom'"
      @mousedown="startSelect"/>
  </div>
</template>

<script>
  import Pin from './Pin'
  export default {
    name: 'CroppedContent',
    props: ['cropImg', 'cropBoxData'],
    methods: {
      onDblclick (e) {
        this.$emit('dblclick', e)
      },
      startSelect (event) {
        console.log(event)
      },
      handleMousMovment (event) {
        console.log(event)
      }
    },
    components: {
      'pin': Pin
    }
  }
</script>

<style>
 .croped-img-container{
    position: absolute;
 }
 .croped-img-container img{
   display: block;
 }
</style>
