<template>

    <div class="badge badge-pill badge-secondary divInput border" :class="borda">
      <span class="btnInput">
        <label class="">{{ descricao }} :</label>
      </span>
      <span class="badge badge-pill badge-ligth inputBtn border" :class="borda" style="font-size:1.7rem; margin-top:1%">
        <label style="margin-top:9%">{{ conteudo }}</label>
      </span>
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
    @media only screen and (max-width: 500px) {
      .divInput{
      font-size: 1.4rem !important;
     }
    }
    .inputBtn{
      background-color: beige;
      color: black;
      height: 70px;
    }
    .btnInput{
      font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
      font-style: italic;
      text-shadow: 0.1em 0.1em 0.05em #333;
      font-size: 2.2rem;

    }
    .divInput{
      width: 90%;
      height: 90px;
      text-align: right;

    }
</style>
