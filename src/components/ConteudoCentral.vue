<template>
  <div class="container">
    <form-01 @calcular="calcular"  />
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
    calcular(obj){
      var fundoGorduraCorporal;
      var textoGorduraCorporal;
      var fundoMassaMagra;     
      var textoMassaMagra;      
      var fundoMassaGorda;
      var textoMassaGorda;
      var fundoImc;
      var textoImc;
      var textoRcq;  
      var fundoRcq;  


      var sexo = obj.iptSexo
      var idade = obj.edtIdade
      var peso = obj.edtPeso
      var altura = obj.edtAltura
      var circunferenciaCintura = obj.edtCircunferenciaCintura
      var exercicios = obj.edtExercicios
      var insonia = (obj.iptInsonia == "sim" ? 0.915 : 1);
      var dormeMal = (obj.iptDormeMal == "sim" ? 0.915 : 1);
      var estresse = (obj.iptEstresse == "sim" ? 0.92 : 1);
      var sanfona = (obj.iptSanfona == "sim" ? 0.9 : 1);
      var alcool = (obj.iptAlcool == "sim" ? 0.95 : 1);
      switch (obj.edtBiotipo) {
        case "ectomorfo":
          var biotipo = 1.1
          break;
        case "mesomorfo":
          var biotipo = 1
          break;      
        case "endomorfo":
          var biotipo = 0.9
          break;      
        default:
          break;
      }
      switch (exercicios) {
        case '1':
          exercicios = 196.875;
          break;
        case '2':
          exercicios = 393.75;
          break;
        case '3':
          exercicios = 135;
          break;
        case '4':
          exercicios = 341.25;
          break;
        case '5':
          exercicios = 525;
          break;
        case '6':
          exercicios = 708.75;
          break;
      
        default:
          break;
      }
      var quadril = obj.edtCircunferenciaQuadril
      var cintura = obj.edtCircunferenciaCintura

      //Tratamentos de exibição
      if(obj.edtObjetivo == "perder"){
        var objetivo = "PERDER PESO"
      }
      if(obj.edtObjetivo == "manter"){
        var objetivo = "MANTER O PESO"
      }
      if(obj.edtObjetivo == "ganhar"){
        var objetivo = "GANHAR PESO"
      }
      var quilosObjetivo = obj.edtQuilosObjetivo
      var rcq = cintura / quadril;
      var percentualGordura = 64 - ((20*altura)/cintura);
      var massaMagra = peso * ( 0.01 * ( 100 - percentualGordura ));
      var massaGorda = peso * ( 0.01 * percentualGordura);

      var imc = peso / ((altura * 0.01)^2)
      // Escolha do sexo
      if(sexo == "masculino"){
        var tmbBase = 66.5 + (13.75 * peso) + (5.003 * altura) - (6.775 * idade)
      }
      if(sexo == "feminino"){
        var tmbBase = 655.1 + (9.563 * peso) + (1.850 * altura) - (4.676 * idade)
      }
      if(percentualGordura > 20 && percentualGordura <= 30){
        fundoGorduraCorporal = 'bg-warning';
        textoGorduraCorporal = 'MEDIO';
      }else if(percentualGordura > 31){
        fundoGorduraCorporal = 'bg-danger';
        textoGorduraCorporal = 'ALTO';
      }else{
        textoGorduraCorporal = 'BOM';
        fundoGorduraCorporal = 'bg-success';
      }
      //
      if(rcq > 20 && rcq <= 30){
        fundoRcq = 'bg-warning';
        textoRcq = 'MEDIO';
      }else if(rcq > 31){
        fundoRcq = 'bg-danger';
        textoRcq = 'ALTO';
      }else{
        textoRcq = 'BOM';
        fundoRcq = 'bg-success';
      }
      //
      if(imc > 20 && imc <= 30){
        fundoImc = 'bg-warning';
        textoImc = 'MEDIO';
      }else if(imc > 31){
        fundoImc = 'bg-danger';
        textoImc = 'ALTO';
      }else{
        textoImc = 'BOM';
        fundoImc = 'bg-success';
      }
      //
      if(massaMagra > 20 && massaMagra <= 30){
        fundoMassaMagra = 'bg-warning';
        textoMassaMagra = 'MEDIO';
      }else if(massaMagra > 31){
        fundoMassaMagra = 'bg-danger';
        textoMassaMagra = 'ALTO';
      }else{
        textoMassaMagra = 'BOM';
        fundoMassaMagra = 'bg-success';
      }
      //
      if(massaGorda > 20 && massaGorda <= 30){
        fundoMassaGorda = 'bg-warning';
        textoMassaGorda = 'MEDIO';
      }else if(massaGorda > 31){
        fundoMassaGorda = 'bg-danger';
        textoMassaGorda = 'ALTO';
      }else{
        textoMassaGorda = 'BOM';
        fundoMassaGorda = 'bg-success';
      }
      

      // Acrescentando o biotipo
      var tmbBase1 = tmbBase * biotipo;

      // Acrescentando os habitos
      var tmbBase2 = tmbBase1 * insonia * estresse * sanfona * alcool;

      var taxaMetabolica = tmbBase2 + exercicios
      var $arrayResult = {};
      $arrayResult = {
        'taxaMetabolica': parseFloat(taxaMetabolica.toFixed(2)),
        'objetivo': objetivo,
        'imc': parseFloat(imc.toFixed(2)),
        'fundoImc': fundoImc,
        'textoImc': textoImc,
        'rcq': parseFloat(rcq.toFixed(2)),
        'fundoRcq': fundoRcq,
        'textoRcq': textoRcq,
        'massaMagra': parseFloat(massaMagra.toFixed(2)),
        'textoMassaMagra': textoMassaMagra,
        'fundoMassaMagra': fundoMassaMagra,
        'massaGorda': parseFloat(massaGorda.toFixed(2)),
        'textoMassaGorda': textoMassaGorda,
        'fundoMassaGorda': fundoMassaGorda,
        'gorduraCorporal': parseFloat(percentualGordura.toFixed(2)),
        'fundoGorduraCorporal': fundoGorduraCorporal,
        'textoGorduraCorporal': textoGorduraCorporal

        }
      
      //console.log($arrayResult);
      this.$emit('exibeResult', $arrayResult)
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
  .video{
    width: 100%;
  }
  .row{
    margin-top: 1rem;
  }
</style>
