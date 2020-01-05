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
      var objetivo = obj.edtObjetivo
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

      // Acrescentando o biotipo
      var tmbBase1 = tmbBase * biotipo;

      // Acrescentando os habitos
      var tmbBase2 = tmbBase1 * insonia * estresse * sanfona * alcool;

      var taxaMetabolica = tmbBase2 + exercicios
      var $arrayResult = {};
      $arrayResult = {
        'taxaMetabolica': parseFloat(taxaMetabolica.toFixed(2)),
        'imc': parseFloat(imc.toFixed(2)),
        'objetivo': objetivo,
        'rcq': parseFloat(rcq.toFixed(2)),
        'gorduraCorporal': parseFloat(percentualGordura.toFixed(2)),
        'massaMagra': parseFloat(massaMagra.toFixed(2)),
        'massaGorda': parseFloat(massaGorda.toFixed(2))

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
