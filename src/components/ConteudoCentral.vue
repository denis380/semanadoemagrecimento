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
      var rangeIdadeGordura;  
      var rangeHomem;
      var percentual;


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
      // ---------------------------------------------------------

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
      // ---------------------------------------------------------
      if(imc > 20.0 && imc <= 29.9){
        fundoImc = 'bg-warning';
        textoImc = 'SOBREPESO';
      }else if(imc > 30.0 && imc <= 34.9){
        fundoImc = 'bg-warning';
        textoImc = 'OBESIDADE GRAU I';
      }else if(imc > 35.0 && imc <= 39.9){
        textoImc = 'OBESIDADE GRAU II';
        fundoImc = 'bg-danger';
      }else if(imc >= 40.0){
        textoImc = 'OBESIDADE GRAU III';
        fundoImc = 'bg-danger';
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

      // Calculo resposta percentual de gordura
      if(idade >= 18 && idade <= 25){
        rangeIdadeGordura = 1;
      }else if(idade >= 26 && idade <= 35){
        rangeIdadeGordura = 2;
      }else if(idade >= 36 && idade <= 45){
        rangeIdadeGordura = 3;
      }else if(idade >= 46 && idade <= 55){
        rangeIdadeGordura = 4;
      }else if(idade >= 56 && idade <= 65){
        rangeIdadeGordura = 5;
      }else{
        rangeIdadeGordura = 0;
      }
      
      // ---------------------------------------------------------
      if(percentualGordura >= 18 && percentualGordura <= 25){
        fundoGorduraCorporal = 'bg-warning';
        textoGorduraCorporal = 'MEDIO';
      }else if(percentualGordura >= 26 && percentualGordura <= 35){
        fundoGorduraCorporal = 'bg-danger';
        textoGorduraCorporal = 'ALTO';
      }else if(percentualGordura >= 36 && percentualGordura <= 45){
        fundoGorduraCorporal = 'bg-danger';
        textoGorduraCorporal = 'ALTO';
      }else if(percentualGordura >= 46 && percentualGordura <= 55){
        fundoGorduraCorporal = 'bg-danger';
        textoGorduraCorporal = 'ALTO';
      }else if(percentualGordura >= 56 && percentualGordura <= 65){
        fundoGorduraCorporal = 'bg-danger';
        textoGorduraCorporal = 'ALTO';
      }else{
        textoGorduraCorporal = '[indefinido]';
        fundoGorduraCorporal = 'bg-ligth';
      }

      switch (true) {
        case (idade > 0 && idade <= 25) :
          percentual = percentual1825(percentualGordura);
          break;
        case (idade <= 35) :
          percentual = percentual2635(percentualGordura);
          break;
        case (idade <= 45) :
          percentual = percentual3645(percentualGordura);
          break;
        case (idade <= 55) :
          percentual = percentual4655(percentualGordura);
          break;
        case (idade <= 65) :
          percentual = percentual5665(percentualGordura);
          break;
      
        default:
          break;
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
        'textoGorduraCorporal': textoGorduraCorporal,
        'percentual' : percentual

        }
        console.log(percentual.fundo);
      
      this.$emit('exibeResult', $arrayResult)
    },
    
  },
}
function percentual1825(percentualGordura){
  switch (true) {
    case (percentualGordura >= 0 && percentualGordura <= 6):
        return {'nivel':'EXCELENTE', 'faixa':'0 a 6%', 'idade': '0 a 25', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 6 && percentualGordura <= 11):
        return {'nivel':'BOM', 'faixa':'7 a 11%', 'idade': '18 a 25', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 11 && percentualGordura <= 14):
        return {'nivel':'ACIMA DA MÉDIA', 'faixa':'12 a 14%', 'idade': '18 a 25', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 14 && percentualGordura <= 16):
        return {'nivel':'MEDIA', 'faixa':'15 a 16%', 'idade': '18 a 25', 'fundo': 'bg-warning'}
      break;
    case (percentualGordura > 16 && percentualGordura <= 20):
        return {'nivel':'ABAIXO DA MÉDIA', 'faixa':'17 a 20%', 'idade': '18 a 25', 'fundo': 'bg-warning'}
      break;
    case (percentualGordura > 20 && percentualGordura <= 24):
        return {'nivel':'RUIM', 'faixa':'20 a 24%', 'idade': '18 a 25', 'fundo': 'bg-danger'}
      break;
    case (percentualGordura > 24 && percentualGordura <= 36):
        return {'nivel':'MUITO RUIM', 'faixa':'25 a 36%', 'idade': '18 a 25', 'fundo': 'bg-danger'}
      break;
  
    default:
      break;
  }
}
function percentual2635(percentualGordura){
   switch (true) {
    case (percentualGordura > 0 && percentualGordura <= 12):
        return {'nivel':'EXCELENTE', 'faixa':'0 a 1%', 'idade': '26 a 35', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 12 && percentualGordura <= 16):
        return {'nivel':'BOM', 'faixa':'12 a 15%', 'idade': '26 a 35', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 16 && percentualGordura <= 18):
        return {'nivel':'ACIMA DA MÉDIA', 'faixa':'16 a 18%', 'idade': '26 a 35', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 18 && percentualGordura <= 21):
        return {'nivel':'MEDIA', 'faixa':'18 a 21%', 'idade': '26 a 35', 'fundo': 'bg-warning'}
      break;
    case (percentualGordura > 21 && percentualGordura <= 24):
        return {'nivel':'ABAIXO DA MÉDIA', 'faixa':'17 a 24%', 'idade': '26 a 35', 'fundo': 'bg-warning'}
      break;
    case (percentualGordura > 24 && percentualGordura <= 28):
        return {'nivel':'RUIM', 'faixa':'24 a 28%', 'idade': '26 a 35', 'fundo': 'bg-danger'}
      break;
    case (percentualGordura > 28 && percentualGordura <= 36):
        return {'nivel':'MUITO RUIM', 'faixa':'25 a 36%', 'idade': '26 a 35', 'fundo': 'bg-danger'}
      break;
  
    default:
      break;
  }
}
function percentual3645(percentualGordura){
   switch (true) {
    case (percentualGordura > 0 && percentualGordura <= 15):
        return {'nivel':'EXCELENTE', 'faixa':'0 a 15%', 'idade': '36 a 45', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 15 && percentualGordura <= 19):
        return {'nivel':'BOM', 'faixa':'15 a 19%', 'idade': '36 a 45', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 19 && percentualGordura <= 21):
        return {'nivel':'ACIMA DA MÉDIA', 'faixa':'19 a 21%', 'idade': '36 a 45', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 21 && percentualGordura <= 23):
        return {'nivel':'MEDIA', 'faixa':'21 a 23%', 'idade': '36 a 45', 'fundo': 'bg-warning'}
      break;
    case (percentualGordura > 24 && percentualGordura <= 26):
        return {'nivel':'ABAIXO DA MÉDIA', 'faixa':'24 a 26%', 'idade': '36 a 45', 'fundo': 'bg-warning'}
      break;
    case (percentualGordura > 26 && percentualGordura <= 29):
        return {'nivel':'RUIM', 'faixa':'26 a 29%', 'idade': '36 a 45', 'fundo': 'bg-danger'}
      break;
    case (percentualGordura > 29 && percentualGordura <= 39):
        return {'nivel':'MUITO RUIM', 'faixa':'29 a 39%', 'idade': '36 a 45', 'fundo': 'bg-danger'}
      break;
  
    default:
      break;
  }
}
function percentual4655(percentualGordura){
   switch (true) {
    case (percentualGordura > 0 && percentualGordura <= 18):
        return {'nivel':'EXCELENTE', 'faixa':'0 a 18%', 'idade': '46 a 55', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 18 && percentualGordura <= 21):
        return {'nivel':'BOM', 'faixa':'18 a 21%', 'idade': '46 a 55', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 21 && percentualGordura <= 23):
        return {'nivel':'ACIMA DA MÉDIA', 'faixa':'21 a 23%', 'idade': '46 a 55', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 23 && percentualGordura <= 25):
        return {'nivel':'MEDIA', 'faixa':'23 a 25%', 'idade': '46 a 55', 'fundo': 'bg-warning'}
      break;
    case (percentualGordura > 25 && percentualGordura <= 27):
        return {'nivel':'ABAIXO DA MÉDIA', 'faixa':'25 a 27%', 'idade': '46 a 55', 'fundo': 'bg-warning'}
      break;
    case (percentualGordura > 27 && percentualGordura <= 30):
        return {'nivel':'RUIM', 'faixa':'27 a 30%', 'idade': '46 a 55', 'fundo': 'bg-danger'}
      break;
    case (percentualGordura > 30 && percentualGordura <= 38):
        return {'nivel':'MUITO RUIM', 'faixa':'30 a 38%', 'idade': '46 a 55', 'fundo': 'bg-danger'}
      break;
  
    default:
      break;
  }
}
function percentual5665(percentualGordura){
   switch (true) {
    case (percentualGordura > 0 && percentualGordura <= 18):
        return {'nivel':'EXCELENTE', 'faixa':'0 a 18%', 'idade': '56 acima', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 18 && percentualGordura <= 21):
        return {'nivel':'BOM', 'faixa':'18 a 21%', 'idade': '56 acima', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 21 && percentualGordura <= 23):
        return {'nivel':'ACIMA DA MÉDIA', 'faixa':'21 a 23%', 'idade': '56 acima', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 21 && percentualGordura <= 25):
        return {'nivel':'MEDIA', 'faixa':'23 a 25%', 'idade': '56 acima', 'fundo': 'bg-warning'}
      break;
    case (percentualGordura > 26 && percentualGordura <= 28):
        return {'nivel':'ABAIXO DA MÉDIA', 'faixa':'26 a 28%', 'idade': '56 acima', 'fundo': 'bg-warning'}
      break;
    case (percentualGordura > 28 && percentualGordura <= 31):
        return {'nivel':'RUIM', 'faixa':'28 a 31%', 'idade': '56 acima', 'fundo': 'bg-danger'}
      break;
    case (percentualGordura > 31 && percentualGordura <= 38):
        return {'nivel':'MUITO RUIM', 'faixa':'31 a 38%', 'idade': '56 acima', 'fundo': 'bg-danger'}
      break;
  
    default:
      break;
  }
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
