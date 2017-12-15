<template>
  <div>
    <div class="image-container">
      <cropper
        v-show="isCropperShow"
        :img="imgSrc"
        @ready="onCropperReady"
        ref="cropper"/>
      <cropped-content
        v-show="!isCropperShow"
        @dblclick="showCropper"
        :crop-box-data="cropBoxData"
        :crop-img="croppedImg"/>
    </div>
    <div
      v-show="isCropperShow"
      class="crop-controls">
      <button @click="save">Ok</button>
      <button @click="cancel">Cancel</button>
    </div>
  </div>

</template>

<script>
  import Cropper from './Cropper'
  import CroppedContent from './CroppedContent'

  export default {
    name: 'page',
    data () {
      return {
        imgSrc: 'static/canva-test.png',
        prevImageDate: null,
        croppedImg: null,
        cropBoxData: null,
        isCropperShow: false
      }
    },
    methods: {
      onCropperReady ({imageData, cropBoxData}) {
        this.cropBoxData = cropBoxData
        this.croppedImg = imageData
      },
      showCropper () {
        this.isCropperShow = true
        this.prevImageDate = this.$refs.cropper.getCroppedCanvas()
      },
      save () {
        this.croppedImg = this.$refs.cropper.getCroppedCanvas()
        this.isCropperShow = false
      },
      cancel () {
        this.croppedImg = this.prevImageDate
        this.isCropperShow = false
      }
    },
    components: {
      'cropper': Cropper,
      'cropped-content': CroppedContent
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
  .image-container{
    position: relative;
  }
</style>
