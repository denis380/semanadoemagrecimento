<template>
    <!--  -->
    <div class="row col-md-12 info-box">
        <div class="col-md-5">

        <div class="row">
            <label class="col-md-4 sexo">SEU BIOTIPO :</label>
              <span class="col-sm-5">
                <select class="custom-select" id="edtBiotipo">
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
                <input type="range" class="custom-range custom-range-danger" id="edtExexcicios" min="0" max="5">
            </span>
        </div>
        <div class="row">
            <label for="edtCircunferenciaQuadril" class="col-md-4 descricao" style="margin-top:-0.3rem">CIRCUNFERÊNCIA DO QUADRIL :</label>
            <span class="col-sm-5 ipt">
            <input id="edtCircunferenciaQuadril" type="number" class="form-control" min="0" max="120">
            </span>
            <span class="descricao" style="margin-left:0.5rem;margin-top:0.3rem">cm</span>
        </div>
        <div class="row">
            <label for="edtObjetivo" class="col-md-4 descricao" style="margin-top:-0.3rem">QUAL É SEU OBJETIVO :</label>
            <span class="col-sm-5">
                <select class="custom-select" id="edtObjetivo">
                    <option value="">- selecione -</option>
                    <option value="perder">Perder Peso</option>
                    <option value="manter">Manter o peso</option>
                    <option value="ganhar">Ganhar peso</option>
                  </select>
              </span>
        </div>
        <div class="row">
            <label for="edtAltura" class="col-md-4 descricao" style="margin-top:-0.3rem">QUANTOS QUILOS :</label>
            <span class="col-sm-5 ipt">
            <input id="edtAltura" type="number" class="form-control" min="0" max="120" >
            </span>
            <span class="descricao" style="margin-left:0.5rem;margin-top:0.3rem">kg</span>
        </div>
        </div>
        
        <div class="col-md-7">
            <div class="embed-responsive embed-responsive-16by9 video">
            <iframe class="embed-responsive-item" :src="urlVideo" allowfullscreen></iframe>
            </div>
        </div>
    </div>

</template>

<script>
export default {
  name: 'Form03',
  components:{
      
  },
  props:[
    'urlVideo',
  ],
  data () {
    return {
      
    }
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
  .ipt{
  }
  .video{
    width: 100%;
  }
  .row{
    margin-top: 1rem;
  }
</style>
