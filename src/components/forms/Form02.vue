<template>
  <div id="app">
  <v-app id="inspire">
    <v-card flat color="transparent">
      <v-card-text>
        <v-slider
          v-model="fruits"
          :tick-labels="ticksLabels"
          :max="5"
          step="1"
          ticks="always"
          tick-size="5"
        ></v-slider>
      </v-card-text>
    </v-card>
  </v-app>
</div>

</template>

<script>
export default {
  name: 'Form01',
  components:{
      
  },
  props:[
    'urlVideo',
  ],
  data () {
    return {
        value: 0,
        fruits: 0,
        ticksLabels: [
          'Figs',
          'Lemon',
          'Pear',
          'Apple',
        ],
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .container{
    margin-top: 5%;
  }
  .title{
    font-size: 1.3rem;
    color: beige;
    padding-bottom: 2rem;
  }
  .form{
    text-align: left;
  }
  .descricao{
    margin-right: 5%;
  }
  .ipt-radio{
    margin-top: 3%;
    margin-right: 5%;
  }
  .video{
    width: 100%;
  }
  .row{
    margin-top: 1rem;
  }
</style>
