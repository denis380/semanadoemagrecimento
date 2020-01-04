<template>
    <span :class=espacos></span>
</template>

<script>
export default {
  name: 'Espaco',
  components:{
      
  },
  props:[
    'espacos'
  ],
  data () {
    return {
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .espaco-0{
      margin-top: 0 !important;
      margin-bottom: 0 !important;
      margin-left: 0 !important;
      margin-right: 0 !important;
    }
    .direita-1{
      margin-right: 1% !important;
    }
    .direita-2{
      margin-right: 2% !important;
    }
    .direita-3{
      margin-right: 3% !important;
    }
    .direita-4{
      margin-right: 4% !important;
    }
    .direita-5{
      margin-right: 5% !important;
    }

    .esquerda-1{
      margin-left: 1% !important;
    }
    .esquerda-2{
      margin-left: 2% !important;
    }
    .esquerda-3{
      margin-left: 3% !important;
    }
    .esquerda-4{
      margin-left: 4% !important;
    }
    .esquerda-5{
      margin-left: 5% !important;
    }
    .top-1{
      margin-top: 1% !important;
    }
    .top-2{
      margin-top: 2% !important;
    }
    .top-3{
      margin-top: 3% !important;
    }
    .top-4{
      margin-top: 4% !important;
    }
    .top-5{
      padding-top: 5% !important;
    }
    .bottom-1{
      margin-bottom: 1% !important;
    }
    .bottom-2{
      margin-bottom: 2% !important;
    }
    .bottom-3{
      margin-bottom: 3% !important;
    }
    .bottom-4{
      margin-bottom: 4% !important;
    }
    .bottom-5{
      margin-bottom: 5% !important;
    }

</style>
