<template>
        <!--  -->
        <div class="container main">
            <div class="card">
                <div class="card-header">
                    <span class="labelResultados">Veja agora o seu resultado em nosso termômetro S2já</span>
                </div>
                <h5 class="card-title main titulo">Esta é sua composição corporal estimada:</h5>
                <!-- /.card-header -->
                <div class="card-body">
                  <table class="table table-bordered">
                    <tbody>
                      <tr>
                        <td class="labelResultados">Percentual de gordura corporal</td>
                        <td class="numeroResultado" :class="fundoGorduraCorporal">
                          <span :class="fundoGorduraCorporal" class="badge"> {{ gorduraCorporal || " ... " }} %</span>
                        </td>
                        <td class="numeroResultado" :class="fundoGorduraCorporal">
                          <span :class="fundoGorduraCorporal" class="badge">{{ textoGorduraCorporal || "..." }}</span>
                        </td>
                      </tr>
    
                      <tr>
                        <td class="labelResultados">Massa magra corporal aproximada</td>
                        <td class="numeroResultado" :class="fundoMassaMagra">
                          <span :class="fundoMassaMagra" class="badge">{{ massaMagra || " ... " }} kg</span>
                          
                        </td>
                        <td class="numeroResultado" :class="fundoMassaMagra"><span :class="fundoMassaMagra" class="badge">{{ textoMassaMagra || "..." }} </span></td>
                      </tr>
    
                      <tr>
                        <td class="labelResultados">Massa gorda corporal aproximada</td>
                        <td class="numeroResultado" :class="fundoMassaGorda">
                            <span :class="fundoMassaGorda" class="badge">{{ massaGorda || " ... " }} kg</span>
                        </td>
                        <td class="numeroResultado" :class="fundoMassaGorda">
                          <span :class="fundoMassaGorda" class="badge">{{ textoMassaGorda || " ... " }} </span>
                        </td>
                      </tr>
    
                      <tr>
                        <td class="labelResultados">Índice de massa corporal (IMC)</td>
                        <td class="numeroResultado" :class="fundoImc">
                            <span :class="fundoImc" class="badge">{{ imc || " ... " }} Kg/m2</span>
                        </td>
                        <td class="numeroResultado" :class="fundoImc">
                          <span :class="fundoImc" class="badge">{{ textoImc || " ... " }}</span>
                        </td>
                      </tr>
                      <tr>
                        <td class="labelResultados">Relação cintura quadril (RCQ)</td>
                        <td class="numeroResultado" :class="fundoRcq">
                          <span :class="fundoRcq" class="badge ">{{ rcq || " ... " }}</span>
                        </td>
                        <td class="numeroResultado" :class="fundoRcq"><span :class="fundoRcq" class="badge ">{{ textoRcq || " ... " }}</span></td>
                      </tr>
    
                    </tbody>
                  </table>
                  <!--  -->
                  <div class="card-header">
                    <h5 class="text-center titulo">Esta é sua taxa metabólica basal estimada: </h5>
                  </div>
                  <div class="card">
                    <table class="margin-full">
                        <tbody>
                          <tr class="">
                            <td class="labelResultados">Quantas calorias o seu corpo consome a cada 24hs</td>
                            <td class="badge-lg bg-warning">
                              <label class="bottom-2 numeroResultado">
                                  {{ taxaMetabolica || " ... " }} 
                                  <span class="badge"> kcal/dia</span>

                              </label>
                            </td>
                          </tr>
                          <hr style="margin-left:15%">
                          <tr>
                            <td class="labelResultados">
                              Esta é a quantidade de quilocalorias que você deve ingerir para conseguir {{ textoObjetivo }}
                              os {{ kgObjetivo }}Kg que você deseja: 
                            </td>
                            <td class="badge-lg bg-success">
                              <label class="bottom-2 numeroResultado">
                                  {{ taxaMetabolicaIndicada || " ... " }} 
                                  <span class="badge"> kcal/dia</span>

                              </label>
                            </td>
                          </tr>
                        </tbody>
                      </table>

                  </div>
                  <!-- <div class="card-header">
                    <h5 class="text-center">SEU OBJETIVO É: </h5>
                  </div>
                  <table class="table table-bordered">
                      <tbody>
                        <tr>
                          <td class="bg-black">
                            {{ objetivo || " ..." }}
                          </td>
                        </tr>
                        <tr >
                          <p class="top-3">
                            Para isso, fique atento à quantidade de macronutrientes que
                            você deve ingerir para conseguir {{ textoObjetivo || "..." }} os {{ kgObjetivo || "0" }} kgs que deseja:
                          </p>
                        </tr>
                      </tbody>
                    </table> -->
                    <div class="col-md-12 row top-3">
                      <div class="col-md-6">
                        <btn-input 
                          borda = "border-danger"
                          descricao = "Proteinas"
                          :conteudo = "'min: ' + proteinas + ' gr/dia'"
                        />
                      </div>
                      <div class="col-md-6">
                        <btn-input 
                          borda = "border-dark"
                          descricao = "Carboidratos"
                          :conteudo = "'max: ' + carboidratos + ' gr/dia'"
                        />
                      </div>
                    </div>
                    <div class="col-md-12 row top-3">
                      <div class="col-md-6">
                        <btn-input 
                          borda = "border-danger"
                          descricao = "Gorduras"
                          :conteudo = "'min: ' + gorduras + ' gr/dia'"
                        />
                      </div>
                      <div class="col-md-6">
                        <btn-input 
                          borda = "border-primary"
                          descricao = "Água"
                          :conteudo = "'max: ' + agua + ' gr/dia'"
                        />
                      </div>
                    </div>

                  <!--  -->
                </div>
                <!-- /.card-body -->
              </div>

          </div>
          <!--  -->
</template>

<script>
import Grafico01 from '@/components/Grafico01'
import BtnInput from '@/components/BtnInput'

export default {
  name: 'Resultado',
  components:{
      Grafico01,
      BtnInput
  },
  props:[
    "gorduraCorporal",
    "textoGorduraCorporal",
    "fundoGorduraCorporal",
    "massaMagra",
    "fundoMassaMagra",
    "textoMassaMagra",
    "massaGorda",
    "fundoMassaGorda",
    "textoMassaGorda",
    "imc",
    "fundoImc",
    "textoImc",
    "taxaMetabolica",
    "objetivo",
    "textoObjetivo",
    "kgObjetivo",
    "proteinas",
    "carboidratos",
    "gorduras",
    "textoRcq",
    "fundoRcq",
    "rcq",
    "agua",
    "dataGrafico01"
  ],
  data () {
    return {
      cores01: ["#41B883", "#E46651","#FFFF00", "#00D8FF"],
      numeros01: [this.proteinas, this.carboidratos, this.gorduras, this.agua],
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .main{
      margin-top: 3%;
    }
    .text-center{
      text-align: center !important;
    }
    .bottom-2{
      margin-bottom: -2%;
    }
    .top-3{
      padding-top: 3%;
    }
    .labelResultados{
      font-size: 1.4rem;
    }
    .numeroResultado{
      font-size: 1.6rem;
    }
    .titulo{
      font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
      font-size: 2.0rem;
    }
    .margin-full{
      width: 90%;
      margin-left: 4%;
      margin-top: 2%;
      margin-bottom: 2%;
    }
</style>
