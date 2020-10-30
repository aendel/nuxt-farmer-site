<template>
  <section class="showcase">
    <div :style="videoContainerClass" class="video-container">
      <video class="bg-video" autoplay muted loop>
        <source :src="videoUrl" type="video/mp4">
      </video>
    </div>
    <div class="content">
      <Hero />
    </div>
  </section>
</template>

<script>
import Hero from '~/components/LayoutComponents/Hero'
export default {
  props:{
    video:{
      type: Object,
      default: () => {}
    }
  },
  components: {
    Hero,
  },
  data(){
    return {
      videoContainerClass:{
        background: `url(${this.imageUrl}) no-repeat center center/cover`
      }
    }
  },
  computed:{
    baseUrl(){
      return 'http://localhost:1337'
    },
    videoUrl(){
      return `${this.baseUrl}${this.video.BackgroundVideo.url}`
    },
    imageUrl(){
      return `${this.baseUrl}${this.video.BackgroundImage.formats.thumbnail.url}`
    }
  }
}
</script>

<style scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.showcase{
  position: relative;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 0 20px;
}

.video-container{
  position: absolute;
  top:0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
  /* background: url('/assets/coverVideo.png') no-repeat center center/cover; */
}

.video-container:after{
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.4);
}

.video-container video{
  min-width: 100%;
  min-height: 100%;
  object-fit: cover;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
}

</style>