<template>
  <div class="principal">
    <cabecalho-principal />

    <texto-central 
      title='Seja bem vindo ao Termômetro S2já!' 
      texto= 'Aqui você ira descobrir como está a saúde do seu metabolismo de forma simples, rápida e direta. 
              Digite as suas medidas e preencha os seus hábitos, para que assim eu consiga analisar as suas tendências 
              metabólicas e te dar uma direção para te orientar rumo à perda de peso!'
    />
    <conteudo-central  />

    <Resultado />

    <Footer />
  </div>
</template>

<script>
import CabecalhoPrincipal from '@/components/cabecalhos/CabecalhoPrincipal'
import TextoCentral from '@/components/cabecalhos/TextoCentral'
import ConteudoCentral from '@/components/ConteudoCentral'
import Resultado from '@/components/Resultado'
import Footer from '@/components/footer'



export default {
  name: 'Principal',
  components:{
    CabecalhoPrincipal,
    TextoCentral,
    ConteudoCentral,
    Footer,
    Resultado

  },
  props:[
    
  ],
  data () {
    return {
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
