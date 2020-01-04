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
                          <span class="badge bg-danger"> {{ gorduraCorporal || "21,5" }} %</span>
                        </td>
                        <td>
                          <span class="badge bg-danger">MEDIO</span>
                        </td>
                      </tr>
    
                      <tr>
                        <td>Massa magra corporal aproximada</td>
                        <td>
                          <span class="badge bg-warning">{{ massasMagra || "74,5" }} Kg</span>
                          
                        </td>
                        <td><span class="badge bg-warning">70%</span></td>
                      </tr>
    
                      <tr>
                        <td>Massa gorda corporal aproximada</td>
                        <td>
                            <span class="badge bg-primary">{{ massaGorda || "20,5" }} Kg</span>
                        </td>
                        <td><span class="badge bg-primary">ALTA</span></td>
                      </tr>
    
                      <tr>
                        <td>Índice de massa corporal (IMC)</td>
                        <td>
                            <span class="badge bg-success">{{ imc || "32,8" }}</span>
                        </td>
                        <td><span class="badge bg-success">SOBREPESO</span></td>
                      </tr>
                      <tr>
                        <td>Relação cintura quadril (RCQ)</td>
                        <td>
                          <span class="badge bg-success">{{ rcq || "0,88" }}</span>
                        </td>
                        <td><span class="badge bg-success">RUIM</span></td>
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
                                {{ taxaMetabolica || "1763" }} 
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
                            {{ objetivo || "EMAGRECIMENTO BRUTO" }}
                          </td>
                        </tr>
                        <tr >
                          <p class="top-3">
                            {{ textoObjetivo || "bla bla bla lorem ipsum dolum sia amet" }}
                          </p>
                        </tr>
                      </tbody>
                    </table>
                    <div class="col-md-12 row top-3">
                      <div class="col-md-4">
                        <label for="">Proteínas</label>
                        <div class="bg-success">{{ proteinas || 154 }} <span class="badge">gr/dia</span></div>
                      </div>
                      <div class="col-md-4">
                        <label for="">Carboidratos</label>
                        <div class="bg-success">{{ carboidratos || 149 }} <span class="badge">gr/dia</span></div>
                      </div>
                      <div class="col-md-4">
                        <label for="">Gorduras</label>
                        <div class="bg-success">{{ gorduras || 29 }} <span class="badge">gr/dia</span></div>
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
    "massaMagra",
    "massaGorda",
    "imc",
    "rcq",
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
