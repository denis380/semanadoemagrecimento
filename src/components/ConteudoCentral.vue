<template>
  <div class="container">
    <form-01 />
  </div>
</template>

<script>

import Form01 from '@/components/forms/Form01'
import Form02 from '@/components/forms/Form02'
import Form03 from '@/components/forms/Form03'

export default {
  name: 'ConteudoCentral',
  components:{
    Form01,
    Form02,
    Form03
  },
  props:[
    'title',
  ],
  data () {
    return {
      
    }
  },
  methods: {
    
  },
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
  .sexo{
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
