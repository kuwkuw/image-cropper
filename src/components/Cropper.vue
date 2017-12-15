<template>
  <div class="cat-container">
    <vue-cropper
      ref="cropper"
      :guides="true"
      :view-mode="1"
      :movable="true"
      :drag-mode="'move'"
      :auto-crop-area="0.5"
      :aspect-ratio="1"
      :min-container-width="800"
      :min-container-height="500"
      :background="false"
      :rotatable="true"
      :crop-box-resizable="false"
      :crop-box-movable="false"
      :ready="ready"
      :src="img"/>
  </div>
</template>

<script>
  export default {
    name: 'cropper',
    props: ['img'],
    methods: {
      ready () {
        const cropBoxData = this.getCropBoxData()
        const imageData = this.getCroppedCanvas()
        this.$emit('ready', { imageData, cropBoxData })
      },
      getCroppedCanvas () {
        return this.$refs.cropper.getCroppedCanvas().toDataURL()
      },
      getCropBoxData () {
        return this.$refs.cropper.getCropBoxData()
      }
    }
  }
</script>

<style>
  .cat-container{
    /* position: absolute;
    top: 0;
    left: 0; */
  }
</style>

