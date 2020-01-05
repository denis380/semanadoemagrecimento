<template>
    <form action="#" @submit.prevent="validaForm">
      <label class="title">Dados antropométricos: Preencha com suas medidas...</label>
      <!-- form 01  -->
      <div class="row col-md-12 info-box">
          <div class="col-md-5">
          <div class="row">
              <label class="col-md-4 sexo">SEXO :</label>
              <div class="form-group form" style='margin-left:0.3rem'>
                  <div class="custom-control custom-radio input-group">
                  <input v-model="iptSexo" class="custom-control-input" type="radio" id="iptMasculino" value="masculino" >
                  <label for="iptMasculino" class="custom-control-label">Masculino</label>
                  </div>
                  <div class="custom-control custom-radio input-group">
                  <input v-model="iptSexo" class="custom-control-input" type="radio" id="iptFeminino" value="feminino" >
                  <label for="iptFeminino" class="custom-control-label">Feminino</label>
                  </div>  
              </div>
          </div>

          <div class="row">
              <label for="edtIdade" class="col-md-4 descricao" style="margin-top:0.3rem">IDADE :</label>
              <span class="col-sm-5">
              <input v-model="edtIdade" :class="{ 'is-invalid' : $v.edtIdade.$invalid }" id="edtIdade" type="number" class="form-control" min="0" max="120">
              </span>
          </div>
          <div class="row">
              <label for="edtPeso" class="col-md-4 descricao" style="margin-top:0.3rem">PESO :</label>
              <span class="col-sm-5">
              <input v-model="edtPeso" id="edtPeso" type="number" :class="{ 'is-invalid' : $v.edtPeso.$invalid }" class="form-control" min="0" max="120">
              </span>
              <span class="descricao" style="margin-left:0.5rem;margin-top:0.3rem">Kg</span>
          </div>
          <div class="row">
              <label for="edtAltura"  class="col-md-4 descricao" style="margin-top:0.3rem">ALTURA :</label>
              <span class="col-sm-5 ipt">
              <input v-model="edtAltura" id="edtAltura" type="number" :class="{ 'is-invalid' : $v.edtAltura.$invalid }" class="form-control" min="0" max="240">
              </span>
          </div>
          <div class="row">
              <label for="edtCircunferenciaCintura" class="col-md-4 descricao">CIRCUNFERÊNCIA DA CINTURA :</label>
              <span class="col-sm-5 ipt">
              <input v-model="edtCircunferenciaCintura" id="edtCircunferenciaCintura" type="number" :class="{ 'is-invalid' : $v.edtCircunferenciaCintura.$invalid }" class="form-control" min="0" max="120" >
              </span>
              <span class="descricao" style="margin-left:0.5rem;margin-top:0.3rem">cm</span>

          </div>
          </div>
          
          <div class="col-md-7">
              <div class="embed-responsive embed-responsive-16by9 video">
              <iframe class="embed-responsive-item" src="https://www.youtube.com/embed/jQ0TyRnw8xU" allowfullscreen></iframe>
              </div>
          </div>
      </div>
      <!-- /form 01 -->
      <!-- form 02 -->
      <hr>
      <label class="title">Hábitos diários : Preencha sobre sua rotina... </label>

      <div class="row col-md-12 info-box">
          <div class="col-md-5">
    
            <div class="row col-md-12">
                <label class="col-md-6 ipt-radio">TÊM INSÔNIA: </label>
                <div class="" style='margin-left:0.3rem'>
                    <div class="custom-control custom-radio input-group">
                    <input v-model="iptInsonia" value='nao' class="custom-control-input" type="radio" id="iptInsoniaNao" name="iptInsonia" >
                    <label for="iptInsoniaNao" class="custom-control-label">Não</label>
                    </div>
                    <div class="custom-control custom-radio input-group">
                    <input v-model="iptInsonia" value='sim' class="custom-control-input" type="radio" id="iptInsoniaSim" name="iptInsonia">
                    <label for="iptInsoniaSim" class="custom-control-label">Sim</label>
                    </div>  
                </div>
            </div>
            <div class="row col-md-12">
                <label class="col-md-6 ipt-radio">DORME MAL : </label>
                <div class="" style='margin-left:0.3rem'>
                    <div class="custom-control custom-radio input-group">
                    <input v-model="iptDormeMal" value='nao' class="custom-control-input" type="radio" id="iptDormeMalNao" name="iptDormeMal" >
                    <label for="iptDormeMalNao" class="custom-control-label">Não</label>
                    </div>
                    <div class="custom-control custom-radio input-group">
                    <input v-model="iptDormeMal" value='sim' class="custom-control-input" type="radio" id="iptDormeMalSim" name="iptDormeMal">
                    <label for="iptDormeMalSim" class="custom-control-label ">Sim</label>
                    </div>  
                </div>
            </div>
            <div class="row col-md-12">
                <label class="col-md-6 ipt-radio" style="margin-top: -0.1rem;">SOFRE ESTRESSE DIÁRIO : </label>
                <div class="" style='margin-left:0.3rem'>
                    <div class="custom-control custom-radio input-group ">
                    <input v-model="iptEstresse" value='nao' class="custom-control-input" type="radio" id="iptEstresseNao" name="iptEstresse" >
                    <label for="iptEstresseNao" class="custom-control-label">Não</label>
                    </div>
                    <div class="custom-control custom-radio input-group ">
                    <input v-model="iptEstresse" value='sim' class="custom-control-input" type="radio" id="iptEstresseSim" name="iptEstresse">
                    <label for="iptEstresseSim" class="custom-control-label ">Sim</label>
                    </div>  
                </div>
            </div>
            <div class="row col-md-12">
                <label class="col-md-6 ipt-radio" style="margin-top: -0.1rem;">SOFRE EFEITO SANFONA : </label>
                <div class="" style='margin-left:0.3rem'>
                    <div class="custom-control custom-radio input-group ">
                    <input v-model="iptSanfona" value='nao' class="custom-control-input" type="radio" id="iptSanfonaNao" name="iptSanfona" >
                    <label for="iptSanfonaNao" class="custom-control-label ">Não</label>
                    </div>
                    <div class="custom-control custom-radio input-group ">
                    <input v-model="iptSanfona" value='sim' class="custom-control-input" type="radio" id="iptSanfonaSim" name="iptSanfona">
                    <label for="iptSanfonaSim" class="custom-control-label ">Sim</label>
                    </div>  
                </div>
            </div>
            <div class="row col-md-12">
                <label class="col-md-6 ipt-radio" style="margin-top: -0.1rem;">CONSOME BEBIDA ALCOÓLICA: </label>
                <div class="" style='margin-left:0.3rem'>
                    <div class="custom-control custom-radio input-group ">
                    <input v-model="iptAlcool" value='nao' class="custom-control-input" type="radio" id="iptAlcoolNao" name="iptAlcool" >
                    <label for="iptAlcoolNao" class="custom-control-label ">Não</label>
                    </div>
                    <div class="custom-control custom-radio input-group ">
                    <input v-model="iptAlcool" value='sim' class="custom-control-input" type="radio" id="iptAlcoolSim" name="iptAlcool">
                    <label for="iptAlcoolSim" class="custom-control-label ">Sim</label>
                    </div>  
                </div>
            </div>
    
          </div>
            
            <div class="col-md-7">
                <div class="embed-responsive embed-responsive-16by9 video">
                <iframe class="embed-responsive-item" src="https://www.youtube.com/embed/jQ0TyRnw8xU" allowfullscreen></iframe>
                </div>
            </div>
        </div>
      <!-- /form 02 -->
      <!-- form 03 -->
      <hr class="hr">
        <label class="title">Genética e objetivos: Deixe eu conhecer você um pouco mais... </label>
        <div class="row col-md-12 info-box">
            <div class="col-md-5">
    
            <div class="row">
                <label class="col-md-4 sexo">SEU BIOTIPO :</label>
                  <span class="col-sm-5">
                    <select v-model="edtBiotipo" :class="{ 'is-invalid' : $v.edtBiotipo.$invalid }" class="custom-select" id="edtBiotipo">
                        <option value="">- selecione -</option>
                        <option value="ectomorfo">Ectomorfo</option>
                        <option value="mesomorfo">Mesomorfo</option>
                        <option value="endomorfo">Endomorfo</option>
                      </select>
                  </span>
            </div>
    
            <div class="row">
                <label for="edtExexcicios" class="col-md-4 descricao" style="margin-top:-0.4rem">EXERCÍCIOS DIARIOS :</label>
                <span class="col-sm-5 ipt">
                    <input v-model="edtExercicios" type="range" class="custom-range custom-range-danger" id="edtExexcicios" min="1" max="6">
                </span>
                <span class="descricao" style="margin-left:0.5rem;margin-top:0.3rem">{{ edtExercicios }}</span>

            </div>
            <div class="row">
                <label for="edtCircunferenciaQuadril" class="col-md-4 descricao" style="margin-top:-0.3rem">CIRCUNFERÊNCIA DO QUADRIL :</label>
                <span class="col-sm-5 ipt">
                <input v-model="edtCircunferenciaQuadril" id="edtCircunferenciaQuadril" type="number" :class="{ 'is-invalid' : $v.edtCircunferenciaQuadril.$invalid }" class="form-control" min="30" max="2000">
                </span>
                <span class="descricao" style="margin-left:0.5rem;margin-top:0.3rem">cm</span>
            </div>
            <div class="row">
                <label for="edtObjetivo" class="col-md-4 descricao" style="margin-top:-0.3rem">QUAL É SEU OBJETIVO :</label>
                <span class="col-sm-5">
                    <select v-model="edtObjetivo" :class="{ 'is-invalid' : $v.edtObjetivo.$invalid }" class="custom-select" id="edtObjetivo">
                        <option value="">- selecione -</option>
                        <option value="perder">Perder Peso</option>
                        <option value="manter">Manter o peso</option>
                        <option value="ganhar">Ganhar peso</option>
                      </select>
                  </span>
            </div>
            <div class="row">
                <label for="edtQuilosObjetivo" class="col-md-4 descricao" style="margin-top:-0.3rem">QUANTOS QUILOS :</label>
                <span class="col-sm-5 ipt">
                <input v-model="edtQuilosObjetivo" id="edtQuilosObjetivo" type="number" :class="{ 'is-invalid' : $v.edtQuilosObjetivo.$invalid }" class="form-control" min="0" max="120" >
                </span>
                <span class="descricao" style="margin-left:0.5rem;margin-top:0.3rem">kg</span>
            </div>
            </div>
            
            <div class="col-md-7">
                <div class="embed-responsive embed-responsive-16by9 video">
                <iframe class="embed-responsive-item" src="https://www.youtube.com/embed/jQ0TyRnw8xU" allowfullscreen></iframe>
                </div>
            </div>
        </div>

      <!-- /form 03 -->
      <hr class="hr">

      <button class="btn btn-block bg-gradient-warning btn-lg">CALCULAR</button>
    </form>

</template>

<script>

import { required, minLength, between } from 'vuelidate/lib/validators'

export default {
  name: 'Form01',
  components:{
      
  },
  data () {
    return {
      iptSexo: "masculino",
      edtIdade: "27",
      edtPeso: "75",
      edtAltura: "170",
      edtCircunferenciaCintura: "70",
      iptInsonia: "nao",
      iptDormeMal: "nao",
      iptEstresse: "nao",
      iptSanfona: "nao",
      iptAlcool: "nao",
      edtBiotipo: "endomorfo",
      edtExercicios: "2",
      edtCircunferenciaQuadril: "75",
      edtObjetivo: "perder",
      edtQuilosObjetivo: "5",
    }
  },
    validations : {
      edtIdade: {
        required
      },
      edtPeso: {
        required
      },
      edtAltura: {
        required
      },
      edtCircunferenciaCintura: {
        required
      },
      edtBiotipo: {
        required
      },
      edtCircunferenciaQuadril: {
        required
      },
      edtObjetivo: {
        required
      },
      edtQuilosObjetivo: {
        required
      },
  },
    methods: {
      validaForm(){
        if(this.isValid){
          this.$emit('calcular', this.$data)
        }
      }
    },
     computed:{
    isValid(){
      return  !this.$v.edtIdade.$invalid &&
              !this.$v.edtPeso.$invalid &&
              !this.$v.edtAltura.$invalid &&
              !this.$v.edtCircunferenciaCintura.$invalid &&
              !this.$v.edtBiotipo.$invalid &&
              !this.$v.edtCircunferenciaQuadril.$invalid &&
              !this.$v.edtObjetivo.$invalid &&
              !this.$v.edtQuilosObjetivo.$invalid

    }
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
  .ipt{
  }
  .video{
    width: 100%;
  }
  .row{
    margin-top: 1rem;
  }

</style>
