<template>
  <v-overlay v-if="loading" :value="loading" class="loading-page">
    <p>Caricamento...</p>
    <Tractor />
  </v-overlay>
</template>

<script>
import Tractor from './Tractor'
export default {
  components:{
    Tractor
  },
  data(){
    return {
      loading: false
    }
  },
  methods: {
    start () {
      this.loading = true
    },
    finish () {
      this.loading = false
    }
  }
}
</script>

<style scoped>
.loading-page {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(255, 255, 255, 0.8);
  text-align: center;
  font-size: 30px;
  font-family: sans-serif;
}
</style>