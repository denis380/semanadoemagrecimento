<template>

    <div class="badge badge-pill badge-secondary divInput border" :class="borda">
      <span class="btnInput">{{ descricao }} :</span>
      <span class="badge badge-pill badge-ligth inputBtn border" :class="borda">{{ conteudo }} </span>
    </div>  
</template>

<script>

export default {
  name: 'BtnInput',
  components:{
      
  },
  props:[
    "borda",
    "descricao",
    "conteudo",
  ],
  data () {
    return {
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .btnInput{
      font-style:sans-serif;
    }
    .inputBtn{
      background-color: beige;
      color: black;
    }
    .divInput{
      width: 90%;
      font-size: 2.0rem;
      text-align: right;
    }
</style>
