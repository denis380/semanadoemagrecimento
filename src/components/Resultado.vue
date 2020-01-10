<template>
        <!--  -->
        <div class="container main">
            <div class="card">
                <div class="card-header">
                  <h3 class="card-title">Veja agora o seu resultado em nosso termômetro S2já</h3>
                </div>
                <h5 class="card-title main">Esta é sua composição corporal estimada:</h5>
                <!-- /.card-header -->
                <div class="card-body">
                  <table class="table table-bordered">
                    <tbody>
                      <tr>
                        <td>Percentual de gordura corporal</td>
                        <td>
                          <span :class="fundoGorduraCorporal" class="badge"> {{ gorduraCorporal || " ... " }} %</span>
                        </td>
                        <td>
                          <span :class="fundoGorduraCorporal" class="badge">{{ textoGorduraCorporal || "..." }}</span>
                        </td>
                      </tr>
    
                      <tr>
                        <td>Massa magra corporal aproximada</td>
                        <td>
                          <span :class="fundoMassaMagra" class="badge">{{ massaMagra || " ... " }} Kg</span>
                          
                        </td>
                        <td><span :class="fundoMassaMagra" class="badge">{{ textoMassaMagra || "..." }}</span></td>
                      </tr>
    
                      <tr>
                        <td>Massa gorda corporal aproximada</td>
                        <td>
                            <span :class="fundoMassaGorda" class="badge">{{ massaGorda || " ... " }} Kg</span>
                        </td>
                        <td><span :class="fundoMassaGorda" class="badge">{{ textoMassaGorda || " ... " }}</span></td>
                      </tr>
    
                      <tr>
                        <td>Índice de massa corporal (IMC)</td>
                        <td>
                            <span :class="fundoImc" class="badge">{{ imc || " ... " }}</span>
                        </td>
                        <td><span :class="fundoImc" class="badge">{{ textoImc || " ... " }}</span></td>
                      </tr>
                      <tr>
                        <td>Relação cintura quadril (RCQ)</td>
                        <td>
                          <span :class="fundoRcq" class="badge ">{{ rcq || " ... " }}</span>
                        </td>
                        <td><span :class="fundoRcq" class="badge ">{{ textoRcq || " ... " }}</span></td>
                      </tr>
    
                    </tbody>
                  </table>
                  <!--  -->
                  <div class="card-header">
                    <h5 class="text-center">Esta é sua taxa metabólica estimada: </h5>
                  </div>
                  <table class="table table-bordered">
                      <tbody>
                        <tr>
                          <td>Quantas calorias o seu corpo consome a cada 24hs</td>
                          <td class="badge-lg bg-warning">
                            <label class="bottom-2">
                                {{ taxaMetabolica || " ... " }} 
                                <span class="badge"> kcal/dia</span>

                            </label>
                          </td>
                        </tr>
                      </tbody>
                    </table>
                  <div class="card-header">
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
                            {{ textoObjetivo || " ... " }}
                          </p>
                        </tr>
                      </tbody>
                    </table>
                    <div class="col-md-12 row top-3">
                      <div class="col-md-4">
                        <label for="">Proteínas</label>
                        <div class="bg-success">{{ proteinas ||  " ... "  }} <span class="badge">gr/dia</span></div>
                      </div>
                      <div class="col-md-4">
                        <label for="">Carboidratos</label>
                        <div class="bg-success">{{ carboidratos || " ... " }} <span class="badge">gr/dia</span></div>
                      </div>
                      <div class="col-md-4">
                        <label for="">Gorduras</label>
                        <div class="bg-success">{{ gorduras || " ... " }} <span class="badge">gr/dia</span></div>
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
export default {
  name: 'Resultado',
  components:{
      
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
    "proteinas",
    "carboidratos",
    "gorduras",
    "textoRcq",
    "fundoRcq",
    "rcq"
  ],
  data () {
    return {
      
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
</style>
