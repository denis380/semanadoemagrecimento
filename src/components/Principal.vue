<template>
  <div class="principal">
    <cabecalho-principal />

    <texto-central 
      title='Seja bem vindo ao Termômetro S2já!' 
      texto= 'Aqui você ira descobrir como está a saúde do seu metabolismo de forma simples, rápida e direta. 
              Digite as suas medidas e preencha os seus hábitos, para que assim eu consiga analisar as suas tendências 
              metabólicas e te dar uma direção para te orientar rumo à perda de peso!'
    />
    <conteudo-central @exibeResult="exibirResult" />

    <Resultado
      v-if="this.exibe"
      v-bind:gorduraCorporal      = 'resultados.gorduraCorporal'
      v-bind:fundoGorduraCorporal = 'resultados.percentual.fundo'
      v-bind:textoGorduraCorporal = 'resultados.percentual.nivel'
      v-bind:massaMagra           = 'resultados.massaMagra'
      v-bind:fundoMassaMagra      = 'resultados.fundoMassaMagra'
      v-bind:textoMassaMagra      = 'resultados.textoMassaMagra'
      v-bind:massaGorda           = 'resultados.massaGorda'
      v-bind:fundoMassaGorda      = 'resultados.fundoMassaGorda'
      v-bind:textoMassaGorda      = 'resultados.textoMassaGorda'
      v-bind:imc                  = 'resultados.imc'
      v-bind:fundoImc             = 'resultados.fundoImc'
      v-bind:textoImc             = 'resultados.textoImc'
      v-bind:rcq                  = 'resultados.rcq'  
      v-bind:textoRcq             = 'resultados.textoRcq'  
      v-bind:fundoRcq             = 'resultados.fundoRcq'  
      v-bind:taxaMetabolica       = 'resultados.taxaMetabolica'
      v-bind:objetivo             = 'resultados.objetivo'
      v-bind:textoObjetivo        = 'resultados.textoObjetivo'
     
     />

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
    'resultados',
    'exibe'
  ],
  data () {
    return {
      
    }
  },
  methods:{
    exibirResult(obj){
      this.resultados = obj;
      switch (obj.objetivo) {
        case 'perder':
          this.resultados.textoObjetivo = 'texto quando quiser perder o peso'
          break;
        case 'manter':
          this.resultados.textoObjetivo = 'texto quando quiser manter o peso'
          break;
        case 'ganhar':
          this.resultados.textoObjetivo = 'texto quando quiser ganhar o peso'
          break;
      
        default:
          break;
      }


      this.exibe = true;
      console.log(this.resultados.rcq)
    },
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
