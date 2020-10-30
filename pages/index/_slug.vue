<template>
  <v-sheet 
    :height="height"
    :elevation="16"
    :id="post"
  >
    <v-container>
    <v-row>
      <v-col>
        <h1>
          {{text}}
        </h1>
      </v-col>
      <v-col>
        <h1>
          {{post}}
        </h1>
      </v-col>
    </v-row>
    </v-container>
  </v-sheet>
</template>

<script>
export default {
  props:{
    post:{
      type: String,
      default: ''
    },
    height:{
      type: Number,
      default: undefined
    }
  },
  data(){
    return{
    }
  },
  computed:{
    text(){
      return this.$route.params
    },
    windowHeightSizeComputed() {
      return window.innerHeight - this.windowOffset
    }
  }
}
</script>

<style>

</style>