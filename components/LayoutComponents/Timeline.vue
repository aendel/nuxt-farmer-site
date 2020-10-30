<template>
  <v-timeline>
    <v-timeline-item v-for="history in histories" :key="history.id" small color="success">
      <!-- <template v-slot:opposite>
        <h2 :class="`headline font-weight-bold`">{{history.title}}</h2>
        <h4>{{history.date}}</h4>
        <p>{{history.description}}</p>
      </template> -->
      <v-card
        shaped
        color="!!light-green accent-1"
        :elevation="20"
      >
          <v-img
            :src="`http://localhost:1337${history.img.formats.small.url}`"
            :lazy-src="`http://localhost:1337${history.img.formats.thumbnail.url}`"
          >
            <template v-slot:placeholder>
              <v-row class="fill-height ma-0" align="center" justify="center">
                <v-progress-circular indeterminate color="light-green darken-2"></v-progress-circular>
              </v-row>
            </template>
          </v-img>
          <v-card-title>
            {{history.title}}
          </v-card-title>
          <v-card-subtitle>
            {{formatDateHistory(history.date)}}
          </v-card-subtitle>
          <v-card-text>
            {{history.description}}
          </v-card-text>
      </v-card>
    </v-timeline-item>
  </v-timeline>
</template>
<script>
export default {
  props:{
    histories:{
      type: Array,
      default: () => []
    }
  },
  data(){
    return{
      target: '#third',
      options: {
        duration: 300,
        offset: 0,
        easing: 'easeInOutCubic',
      }
    }
  },
  methods:{
    formatDateHistory(date){
      return date ? new Date(date).toLocaleDateString() : '' 
    }
  }
}
</script>
<style scoped>

</style>