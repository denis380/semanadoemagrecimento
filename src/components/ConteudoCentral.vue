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
      var respostaRcq;
      var percentualGordura;

      var kgObjetivo = obj.edtQuilosObjetivo;
      var sexo = obj.iptSexo
      var idade = obj.edtIdade
      var peso = obj.edtPeso
      var altura = obj.edtAltura
      var circunferenciaCintura = obj.edtCircunferenciaCintura
      var exercicios = obj.edtExercicios
      var insonia = (obj.iptInsonia == "sim" ? 0.915 : 1);
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
          exercicios = 0;
          break;
        case '2':
          exercicios = 165;
          break;
        case '3':
          exercicios = 225;
          break;
        case '4':
          exercicios = 341;
          break;
        case '5':
          exercicios = 459;
          break;
        case '6':
          exercicios = 630;
          break;
        case '7':
          exercicios = 1063;
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
        var objetivo = "MANTER O PESO";
      }
      if(obj.edtObjetivo == "ganhar"){
        var objetivo = "GANHAR PESO";
      }
      var quilosObjetivo = obj.edtQuilosObjetivo;
      var rcq = cintura / quadril;
      var percentualGordura = 64 - ((20*altura)/cintura);
      var massaMagraBase = peso * ( 0.01 * ( 100 - percentualGordura ));
      var massaGordaBase = peso * ( 0.01 * percentualGordura);
      var massaMagra = (massaMagraBase * 100) / peso;
      var massaGorda = (massaGordaBase * 100) / peso;
      var massaMagraKg = (peso / 100) * massaMagra;
      var massaGordaKg = (peso / 100) * massaGorda;
      var objetivoValor = obj.edtObjetivo;

      var imc = peso / ((altura * 0.01)^2);
      // Escolha do sexo
      if(sexo == "masculino"){
        var tmbBase = parseInt(66.5 + (13.75 * peso) + (5.003 * altura) - (6.775 * idade));
      }
      if(sexo == "feminino"){
        var tmbBase = parseInt(655.1 + (9.563 * peso) + (1.850 * altura) - (4.676 * idade));
      }
      // ---------------------------------------------------------
      if(imc > 0 && imc <= 30){
        fundoImc = 'bg-warning';
        textoImc = 'SOBREPESO';
      }else if(imc > 30 && imc <= 35){
        fundoImc = 'bg-warning';
        textoImc = 'OBESIDADE GRAU I';
      }else if(imc > 35 && imc <= 40){
        textoImc = 'OBESIDADE GRAU II';
        fundoImc = 'bg-danger';
      }else if(imc > 40){
        textoImc = 'OBESIDADE GRAU III';
        fundoImc = 'bg-danger';
      }else{ 
        textoImc = 'INDEFINIDO';
        fundoImc = 'bg-ligth'
      }
      //
      if(massaMagra < 90 && massaMagra >= 70){
        fundoMassaMagra = 'bg-success';
        textoMassaMagra = 'BOM';
      }else if(massaMagra < 70){
        fundoMassaMagra = 'bg-warning';
        textoMassaMagra = 'MEDIA';
      }else{
        fundoMassaMagra = 'bg-danger';
        textoMassaMagra = 'RUIM';
      }
      //
      if(massaGorda > 0 && massaGorda <= 10){
        fundoMassaGorda = 'bg-success';
        textoMassaGorda = 'BOM';
      }else if(massaGorda > 10 && massaGorda <= 30){
        fundoMassaGorda = 'bg-warning';
        textoMassaGorda = 'MEDIA';
      }else{
        fundoMassaGorda = 'bg-warning';
        textoMassaGorda = 'RUIM';
      }

      switch (true) {
        case (idade > 0 && idade <= 25) :
          if(sexo == 'masculino'){
            percentual = percentual1825(percentualGordura);
          }else{
            percentual = fpercentual1825(percentualGordura);
          }
          break;
        case (idade <= 35) :
          if(sexo == 'masculino'){
            percentual = percentual2635(percentualGordura);
          }else{
            percentual = fpercentual2635(percentualGordura);
          }
          break;
        case (idade <= 45) :
          if(sexo == 'masculinoM'){
            percentual = percentual3645(percentualGordura);
          }else{
            percentual = fpercentual3645(percentualGordura);
          }
          break;
        case (idade <= 55) :
          if(sexo == 'masculino'){
            percentual = percentual4655(percentualGordura);
          }else{
            percentual = fpercentual4655(percentualGordura);
          }
          break;
        case (idade <= 65) :
          if(sexo == 'masculino'){
            percentual = percentual5665(percentualGordura);
          }else{
            percentual = fpercentual5665(percentualGordura);
          }
          break;
      
        default:
          break;
      }
      // Pegando resposta do RCQ
      switch (true) {
        case (idade > 0 && idade <= 29) :
          if(sexo == 'masculino'){
            respostaRcq = rcq0029(rcq);
          }else{
            respostaRcq = frcq0029(rcq);
          }
          break;
        case (idade <= 39) :
          if(sexo == 'masculino'){
            respostaRcq = rcq2939(rcq);
          }else{
            respostaRcq = frcq2939(rcq);
          }
          break;
        case (idade <= 49) :
          if(sexo == 'masculino'){
            respostaRcq = rcq3949(rcq);
          }else{
            respostaRcq = frcq0029(rcq);
          }
          break;
        case (idade <= 59) :
          if(sexo == 'masculino'){
            respostaRcq = rcq4959(rcq);
          }else{
            respostaRcq = frcq4959(rcq);
          }
          break;
        default:
          if(sexo == 'masculino'){
            respostaRcq = rcq5969(rcq);
          }else{
            respostaRcq = frcq5969(rcq);
          }
          break;
      }
      

      // Acrescentando o biotipo
      var tmbBase1 = parseInt(tmbBase * biotipo);

      // Acrescentando os habitos
      var tmbBase2 = tmbBase1 * insonia * estresse * sanfona * alcool;

      var taxaMetabolica = tmbBase2 + exercicios
      var carboidratos = getCarboidratos(taxaMetabolica, objetivoValor);
      var proteinas = getProteinas(taxaMetabolica, objetivoValor);
      var gorduras = getGorduras(taxaMetabolica, objetivoValor);
      var agua = getAgua(peso, objetivoValor);
      var $arrayResult = {};
      $arrayResult = {
        'taxaMetabolica': parseFloat(taxaMetabolica.toFixed(1)),
        'objetivo': objetivo,
        'textoObjetivo': obj.edtObjetivo,
        'kgObjetivo': kgObjetivo,
        'imc': parseFloat(imc.toFixed(1)),
        'fundoImc': fundoImc,
        'textoImc': textoImc,
        'rcq': parseFloat(rcq.toFixed(1)),
        'fundoRcq': fundoRcq,
        'textoRcq': textoRcq,
        'massaMagra': parseFloat(massaMagraKg.toFixed(1)),
        'textoMassaMagra': textoMassaMagra,
        'fundoMassaMagra': fundoMassaMagra,
        'massaGorda': parseFloat(massaGordaKg.toFixed(1)),
        'textoMassaGorda': textoMassaGorda,
        'fundoMassaGorda': fundoMassaGorda,
        'gorduraCorporal': parseFloat(percentualGordura.toFixed(1)),
        'fundoGorduraCorporal': fundoGorduraCorporal,
        'textoGorduraCorporal': textoGorduraCorporal,
        'percentual' : percentual,
        'respostaRcq' : respostaRcq,
        'carboidratos' : parseInt(carboidratos),
        'proteinas' : parseInt(proteinas),
        'gorduras' : parseInt(gorduras),
        'agua': parseFloat(agua.toFixed(1))

        }
        //console.log(percentual.fundo);
      
      this.$emit('exibeResult', $arrayResult)
    },
    
  },
}
// Função para homens 
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
    case (percentualGordura > 24):
        return {'nivel':'MUITO RUIM', 'faixa':'25 a 36%', 'idade': '18 a 25', 'fundo': 'bg-danger'}
      break;
  
    default:
      break;
  }
}
function percentual2635(percentualGordura){
   switch (true) {
    case (percentualGordura > 0 && percentualGordura <= 12):
        return {'nivel':'EXCELENTE', 'faixa':'0 a 12%', 'idade': '26 a 35', 'fundo': 'bg-success'}
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
    case (percentualGordura > 28):
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
    case (percentualGordura > 29):
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
    case (percentualGordura > 30):
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
    case (percentualGordura > 31):
        return {'nivel':'MUITO RUIM', 'faixa':'31 a 38%', 'idade': '56 acima', 'fundo': 'bg-danger'}
      break;
  
    default:
      break;
  }
}
// Função para mulheres
function fpercentual1825(percentualGordura){
  switch (true) {
    case (percentualGordura >= 0 && percentualGordura <= 16):
        return {'nivel':'EXCELENTE', 'faixa':'0 a 16%', 'idade': '18 a 25', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 16 && percentualGordura <= 19):
        return {'nivel':'BOM', 'faixa':'16 a 19%', 'idade': '18 a 25', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 19 && percentualGordura <= 22):
        return {'nivel':'ACIMA DA MÉDIA', 'faixa':'19 a 22%', 'idade': '18 a 25', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 22 && percentualGordura <= 25):
        return {'nivel':'MEDIA', 'faixa':'22 a 25%', 'idade': '18 a 25', 'fundo': 'bg-warning'}
      break;
    case (percentualGordura > 26 && percentualGordura <= 28):
        return {'nivel':'ABAIXO DA MÉDIA', 'faixa':'26 a 28%', 'idade': '18 a 25', 'fundo': 'bg-warning'}
      break;
    case (percentualGordura > 29 && percentualGordura <= 31):
        return {'nivel':'RUIM', 'faixa':'29 a 31%', 'idade': '18 a 25', 'fundo': 'bg-danger'}
      break;
    case (percentualGordura > 33):
        return {'nivel':'MUITO RUIM', 'faixa':'33 a 43%', 'idade': '18 a 25', 'fundo': 'bg-danger'}
      break;
  
    default:
      break;
  }
}
function fpercentual2635(percentualGordura){
   switch (true) {
    case (percentualGordura > 0 && percentualGordura <= 16):
        return {'nivel':'EXCELENTE', 'faixa':'0 a 16%', 'idade': '26 a 35', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 16 && percentualGordura <= 20):
        return {'nivel':'BOM', 'faixa':'16 a 20%', 'idade': '26 a 35', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 20 && percentualGordura <= 23):
        return {'nivel':'ACIMA DA MÉDIA', 'faixa':'20 a 23%', 'idade': '26 a 35', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 23 && percentualGordura <= 25):
        return {'nivel':'MEDIA', 'faixa':'23 a 25%', 'idade': '26 a 35', 'fundo': 'bg-warning'}
      break;
    case (percentualGordura > 25 && percentualGordura <= 29):
        return {'nivel':'ABAIXO DA MÉDIA', 'faixa':'25 a 29%', 'idade': '26 a 35', 'fundo': 'bg-warning'}
      break;
    case (percentualGordura > 29 && percentualGordura <= 35):
        return {'nivel':'RUIM', 'faixa':'29 a 35%', 'idade': '26 a 35', 'fundo': 'bg-danger'}
      break;
    case (percentualGordura > 35):
        return {'nivel':'MUITO RUIM', 'faixa':'35 a 49%', 'idade': '26 a 35', 'fundo': 'bg-danger'}
      break;
  
    default:
      break;
  }
}
function fpercentual3645(percentualGordura){
   switch (true) {
    case (percentualGordura > 0 && percentualGordura <= 19):
        return {'nivel':'EXCELENTE', 'faixa':'0 a 19%', 'idade': '36 a 45', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 19 && percentualGordura <= 23):
        return {'nivel':'BOM', 'faixa':'19 a 23%', 'idade': '36 a 45', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 23 && percentualGordura <= 26):
        return {'nivel':'ACIMA DA MÉDIA', 'faixa':'23 a 26%', 'idade': '36 a 45', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 26 && percentualGordura <= 29):
        return {'nivel':'MEDIA', 'faixa':'26 a 29%', 'idade': '36 a 45', 'fundo': 'bg-warning'}
      break;
    case (percentualGordura > 29 && percentualGordura <= 32):
        return {'nivel':'ABAIXO DA MÉDIA', 'faixa':'29 a 32%', 'idade': '36 a 45', 'fundo': 'bg-warning'}
      break;
    case (percentualGordura > 32 && percentualGordura <= 36):
        return {'nivel':'RUIM', 'faixa':'32 a 36%', 'idade': '36 a 45', 'fundo': 'bg-danger'}
      break;
    case (percentualGordura > 36):
        return {'nivel':'MUITO RUIM', 'faixa':'36 a 48%', 'idade': '36 a 45', 'fundo': 'bg-danger'}
      break;
  
    default:
      break;
  }
}
function fpercentual4655(percentualGordura){
   switch (true) {
    case (percentualGordura > 0 && percentualGordura <= 21):
        return {'nivel':'EXCELENTE', 'faixa':'0 a 21%', 'idade': '46 a 55', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 21 && percentualGordura <= 25):
        return {'nivel':'BOM', 'faixa':'21 a 25%', 'idade': '46 a 55', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 25 && percentualGordura <= 28):
        return {'nivel':'ACIMA DA MÉDIA', 'faixa':'25 a 28%', 'idade': '46 a 55', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 28 && percentualGordura <= 31):
        return {'nivel':'MEDIA', 'faixa':'28 a 31%', 'idade': '46 a 55', 'fundo': 'bg-warning'}
      break;
    case (percentualGordura > 32 && percentualGordura <= 34):
        return {'nivel':'ABAIXO DA MÉDIA', 'faixa':'31 a 34%', 'idade': '46 a 55', 'fundo': 'bg-warning'}
      break;
    case (percentualGordura > 34 && percentualGordura <= 39):
        return {'nivel':'RUIM', 'faixa':'34 a 39%', 'idade': '46 a 55', 'fundo': 'bg-danger'}
      break;
    case (percentualGordura > 39):
        return {'nivel':'MUITO RUIM', 'faixa':'39 a 50%', 'idade': '46 a 55', 'fundo': 'bg-danger'}
      break;
  
    default:
      break;
  }
}
function fpercentual5665(percentualGordura){
   switch (true) {
    case (percentualGordura > 0 && percentualGordura <= 23):
        return {'nivel':'EXCELENTE', 'faixa':'0 a 23%', 'idade': '56 acima', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 23 && percentualGordura <= 26):
        return {'nivel':'BOM', 'faixa':'23 a 26%', 'idade': '56 acima', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 26 && percentualGordura <= 29):
        return {'nivel':'ACIMA DA MÉDIA', 'faixa':'26 a 29%', 'idade': '56 acima', 'fundo': 'bg-success'}
      break;
    case (percentualGordura > 29 && percentualGordura <= 32):
        return {'nivel':'MEDIA', 'faixa':'29 a 32%', 'idade': '56 acima', 'fundo': 'bg-warning'}
      break;
    case (percentualGordura > 32 && percentualGordura <= 35):
        return {'nivel':'ABAIXO DA MÉDIA', 'faixa':'32 a 35%', 'idade': '56 acima', 'fundo': 'bg-warning'}
      break;
    case (percentualGordura > 35 && percentualGordura <= 39):
        return {'nivel':'RUIM', 'faixa':'35 a 39%', 'idade': '56 acima', 'fundo': 'bg-danger'}
      break;
    case (percentualGordura > 39):
        return {'nivel':'MUITO RUIM', 'faixa':'39 a 49%', 'idade': '56 acima', 'fundo': 'bg-danger'}
      break;
  
    default:
      break;
  }
}

function rcq0029(rcq){
   switch (true) {
    case (rcq > 0 && rcq <= 0.83):
        return {'nivel':'BAIXO RISCO', 'fundo': 'bg-success'}
      break;
    case (rcq < 0.88):
        return {'nivel':'MODERADO','fundo': 'bg-warning'}
      break;
    case (rcq < 0.94):
        return {'nivel':'ALTO RISCO',  'fundo': 'bg-danger'}
      break;
    default:
        return {'nivel':'MUITO ALTO', 'fundo': 'bg-danger'}
      break;
  }
}
function rcq2939(rcq){
   switch (true) {
    case (rcq > 0 && rcq <= 0.84):
        return {'nivel':'BAIXO RISCO', 'fundo': 'bg-success'}
      break;
    case (rcq < 0.91):
        return {'nivel':'MODERADO','fundo': 'bg-warning'}
      break;
    case (rcq < 0.96):
        return {'nivel':'ALTO RISCO',  'fundo': 'bg-danger'}
      break;
    default:
        return {'nivel':'MUITO ALTO', 'fundo': 'bg-danger'}
      break;
  }
}
function rcq3949(rcq){
   switch (true) {
    case (rcq > 0 && rcq <= 0.88):
        return {'nivel':'BAIXO RISCO', 'fundo': 'bg-success'}
      break;
    case (rcq < 0.95):
        return {'nivel':'MODERADO','fundo': 'bg-warning'}
      break;
    case (rcq < 1):
        return {'nivel':'ALTO RISCO',  'fundo': 'bg-danger'}
      break;
    default:
        return {'nivel':'MUITO ALTO', 'fundo': 'bg-danger'}
      break;
  }
}
function rcq4959(rcq){
   switch (true) {
    case (rcq > 0 && rcq <= 0.90):
        return {'nivel':'BAIXO RISCO', 'fundo': 'bg-success'}
      break;
    case (rcq < 0.96):
        return {'nivel':'MODERADO','fundo': 'bg-warning'}
      break;
    case (rcq < 1.02):
        return {'nivel':'ALTO RISCO',  'fundo': 'bg-danger'}
      break;
    default:
        return {'nivel':'MUITO ALTO', 'fundo': 'bg-danger'}
      break;
  }
}
function rcq5969(rcq){
   switch (true) {
    case (rcq > 0 && rcq <= 0.91):
        return {'nivel':'BAIXO RISCO', 'fundo': 'bg-success'}
      break;
    case (rcq < 0.98):
        return {'nivel':'MODERADO','fundo': 'bg-warning'}
      break;
    case (rcq < 1.03):
        return {'nivel':'ALTO RISCO',  'fundo': 'bg-danger'}
      break;
    default:
        return {'nivel':'MUITO ALTO', 'fundo': 'bg-danger'}
      break;
  }
}

function frcq0029(rcq){
   switch (true) {
    case (rcq > 0 && rcq <= 0.71):
        return {'nivel':'BAIXO RISCO', 'fundo': 'bg-success'}
      break;
    case (rcq < 0.77):
        return {'nivel':'MODERADO','fundo': 'bg-warning'}
      break;
    case (rcq < 0.82):
        return {'nivel':'ALTO RISCO',  'fundo': 'bg-danger'}
      break;
    default:
        return {'nivel':'MUITO ALTO', 'fundo': 'bg-danger'}
      break;
  }
}
function frcq2939(rcq){
   switch (true) {
    case (rcq > 0 && rcq <= 0.72):
        return {'nivel':'BAIXO RISCO', 'fundo': 'bg-success'}
      break;
    case (rcq < 0.78):
        return {'nivel':'MODERADO','fundo': 'bg-warning'}
      break;
    case (rcq < 0.84):
        return {'nivel':'ALTO RISCO',  'fundo': 'bg-danger'}
      break;
    default:
        return {'nivel':'MUITO ALTO', 'fundo': 'bg-danger'}
      break;
  }
}
function frcq3949(rcq){
   switch (true) {
    case (rcq > 0 && rcq <= 0.73):
        return {'nivel':'BAIXO RISCO', 'fundo': 'bg-success'}
      break;
    case (rcq < 0.79):
        return {'nivel':'MODERADO','fundo': 'bg-warning'}
      break;
    case (rcq < 87):
        return {'nivel':'ALTO RISCO',  'fundo': 'bg-danger'}
      break;
    default:
        return {'nivel':'MUITO ALTO', 'fundo': 'bg-danger'}
      break;
  }
}
function frcq4959(rcq){
   switch (true) {
    case (rcq > 0 && rcq <= 0.74):
        return {'nivel':'BAIXO RISCO', 'fundo': 'bg-success'}
      break;
    case (rcq < 0.81):
        return {'nivel':'MODERADO','fundo': 'bg-warning'}
      break;
    case (rcq < 0.88):
        return {'nivel':'ALTO RISCO',  'fundo': 'bg-danger'}
      break;
    default:
        return {'nivel':'MUITO ALTO', 'fundo': 'bg-danger'}
      break;
  }
}
function frcq5969(rcq){
   switch (true) {
    case (rcq > 0 && rcq <= 0.76):
        return {'nivel':'BAIXO RISCO', 'fundo': 'bg-success'}
      break;
    case (rcq < 0.83):
        return {'nivel':'MODERADO','fundo': 'bg-warning'}
      break;
    case (rcq < 0.90):
        return {'nivel':'ALTO RISCO',  'fundo': 'bg-danger'}
      break;
    default:
        return {'nivel':'MUITO ALTO', 'fundo': 'bg-danger'}
      break;
  }
}
function getProteinas(taxaMetabolica, objetivo){
  var proteinas = ((taxaMetabolica / 100 ) * 30) / 4;
  switch (objetivo) {
    case 'perder':
      return proteinas;
      break;
    case 'manter':
      return proteinas;
      break;
    case 'ganhar':
      proteinas = (((taxaMetabolica / 100 ) * 35) / 4) * 1.2;
      return proteinas;
      break;
  
    default:
      break;
  }
}
function getCarboidratos(taxaMetabolica, objetivo){
  //ajeitar a porcentagem
  var carboidratos = ((taxaMetabolica / 100 ) * 50) / 4;
    switch (objetivo) {
    case 'perder':
      carboidratos = carboidratos * 0.7;
      return carboidratos;
      break;
    case 'manter':
      return carboidratos;
      break;
    case 'ganhar':
      carboidratos = (((taxaMetabolica / 100 ) * 45) / 4) * 1.7;
      return carboidratos;
      break;
  
    default:
      break;
  }
}
function getGorduras(taxaMetabolica, objetivo){
    //ajeitar a porcentagem
  var gorduras = ((taxaMetabolica / 100 ) * 20) / 9;
    switch (objetivo) {
    case 'perder':
      gorduras = gorduras * 0.75;
      return gorduras;
      break;
    case 'manter':
      return gorduras;
      break;
    case 'ganhar':
      gorduras = gorduras * 0.9;
      return gorduras;
      break;
  
    default:
      break;
  }
}
function getAgua(peso, objetivo){
  var agua;
  switch (objetivo) {
    case 'perder':
      agua = peso * 0.06;
      return agua;
      break;
    case 'manter':
      agua = peso * 0.05;
      return agua;
      break;
    case 'ganhar':
      agua = peso * 0.07;
      return agua;
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
