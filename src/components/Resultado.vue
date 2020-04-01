<template>
  <!--  -->
  <div class="container main">
    <div class="card">
      <div class="card-header">
        <span class="labelResultados">Veja agora o seu resultado em nosso termômetro S2já</span>
      </div>
      <h5
        class="card-title main titulo top-3"
        id="focus"
        name="focus"
      >Esta é sua composição corporal estimada:</h5>
      <!-- /.card-header -->
      <div class="card-body">
        <table class="table table-bordered">
          <tbody>
            <tr>
              <td class="labelResultados">Percentual de gordura corporal</td>
              <td class="numeroResultado" :class="fundoGorduraCorporal">
                <span :class="fundoGorduraCorporal" class="badge">{{ gorduraCorporal || " ... " }} %</span>
              </td>
              <td class="numeroResultado" :class="fundoGorduraCorporal">
                <span
                  :class="fundoGorduraCorporal"
                  class="badge"
                >{{ textoGorduraCorporal || "..." }}</span>
              </td>
            </tr>

            <tr>
              <td class="labelResultados">Massa magra corporal aproximada</td>
              <td class="numeroResultado" :class="fundoMassaMagra">
                <span :class="fundoMassaMagra" class="badge">{{ massaMagra || " ... " }} kg</span>
              </td>
              <td class="numeroResultado" :class="fundoMassaMagra">
                <span :class="fundoMassaMagra" class="badge">{{ textoMassaMagra || "..." }}</span>
              </td>
            </tr>

            <tr>
              <td class="labelResultados">Massa gorda corporal aproximada</td>
              <td class="numeroResultado" :class="fundoMassaGorda">
                <span :class="fundoMassaGorda" class="badge">{{ massaGorda || " ... " }} kg</span>
              </td>
              <td class="numeroResultado" :class="fundoMassaGorda">
                <span :class="fundoMassaGorda" class="badge">{{ textoMassaGorda || " ... " }}</span>
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
                <span :class="fundoRcq" class="badge">{{ rcq || " ... " }}</span>
              </td>
              <td class="numeroResultado" :class="fundoRcq">
                <span :class="fundoRcq" class="badge">{{ textoRcq || " ... " }}</span>
              </td>
            </tr>
          </tbody>
        </table>
        <!--  -->
        <div class="card-header">
          <h5 class="text-center titulo top-3">Esta é sua taxa metabólica basal estimada:</h5>
        </div>
        <div class="card">
          <table class="margin-full">
            <tbody>
              <tr class>
                <td class="labelResultados">Quantas calorias o seu corpo consome a cada 24hs</td>
                <td class="badge-lg bg-warning">
                  <label class="bottom-2 numeroResultado">
                    {{ taxaMetabolica || " ... " }}
                    <span class="badge">kcal/dia</span>
                  </label>
                </td>
              </tr>
              <hr style="margin-left:15%" />
              <tr>
                <td class="labelResultados">
                  Esta é a quantidade de quilocalorias que você deve ingerir para conseguir {{ textoObjetivo }}
                  os {{ kgObjetivo }}Kg que você deseja:
                </td>
                <td class="badge-lg bg-success">
                  <label class="bottom-2 numeroResultado">
                    {{ taxaMetabolicaIndicada || " ... " }}
                    <span class="badge">kcal/dia</span>
                  </label>
                </td>
              </tr>
            </tbody>
          </table>
        </div>

        <div class="col-md-12 row top-3">
          <div class="col-md-6">
            <btn-input
              borda="border-danger"
              descricao="Proteinas"
              :conteudo="'min: ' + proteinas + ' gr/dia'"
            />
          </div>
          <div class="col-md-6">
            <btn-input
              borda="border-dark"
              descricao="Carboidratos"
              :conteudo="'max: ' + carboidratos + ' gr/dia'"
            />
          </div>
        </div>
        <div class="col-md-12 row top-3">
          <div class="col-md-6">
            <btn-input
              borda="border-danger"
              descricao="Gorduras"
              :conteudo="'max: ' + gorduras + ' gr/dia'"
            />
          </div>
          <div class="col-md-6">
            <btn-input
              borda="border-primary"
              descricao="Água"
              :conteudo="'média: ' + agua + ' Lt/dia'"
            />
          </div>
        </div>
        <hr />
        <div class="container text-center" style="width:50%">
          <div class="embed-responsive embed-responsive-16by9 video">
            <iframe
              class="embed-responsive-item"
              src="https://www.youtube.com/embed/V7nhPVIvmzI"
              allowfullscreen
            ></iframe>
          </div>
        </div>
        <div class="container">
          <h5 class="text-center titulo top-3">Ainda não acabou!</h5>
          <p class="textoAlimentos">
            Eu separei para você um comparativo com os principais alimentos que estão presentes em nossa mesa,
            para ajudar você a fazer a melhor escolha quando for se alimentar. Fique atento aos alimentos que te ajudam a alcançar o
            seu objetivo ( BONS ) e aqueles que te atrapalham e naturalmente, são os menos indicados ( RUINS ).
          </p>
        </div>

        <div class="col-md-12 row top-3">
          <div class="col-md-6">
            <img src="/static/img/proteinas.png" alt="Proteinas" class="img-thumbnail" />
          </div>
          <div class="col-md-6">
            <img src="/static/img/carboidratos.png" alt="Proteinas" class="img-thumbnail" />
          </div>
        </div>
        <hr />
        <div class="col-md-12 row">
          <div class="col-md-6">
            <img src="/static/img/gorduras.png" alt="Proteinas" class="img-thumbnail" />
          </div>
          <div class="col-md-6">
            <img src="/static/img/agua.png" alt="Proteinas" class="img-thumbnail" />
          </div>
        </div>
        <!--  -->
        <div class="container livro">

          <div class="col-md-12 row">
            <div class="col-md-8">
              <p id="textoDowload">
                Agora que você já entendeu como seu organismo funciona, eu tenho um presente para você! Eu escrevi um E-book,
                e nele eu irei te ensinar de forma simples,o que você deve fazer para acelerar seu metabolismo obter resultados
                de forma fácil, prática e sem sofrimentos! Baixe agora!
              </p>
            </div>
            <div class="col-md-4">
              <img
                src="/static/img/livro.png"
                alt="ebook SuperSaude"
                id="imgLivro"
                class="img-thumbnail"
              />
            </div>
          </div>
        </div>
        <div class="btnDownload">
          <img src="static/img/botao_download.png" alt="..." id="imgDownload" v-on:click='redireciona()'>
        </div>
        <div>
          <hr style="width: 50%;">
          <h4>Muito obrigado pelo acesso!</h4> 
          <h5>Acesse agora nossas referências e base de dados.</h5>  
        </div>
        <div class="col-md-12 row" style="margin-top:5%">
          <div class="col-md-6 badge badge-info text-center" style="font-size: 1rem;white-space: normal;cursor: default;" v-on:click='downloadBase()'>
            <p>
              Clique aqui para acessar a base científica que utilizei para estruturar os cálculos
            </p>
          </div>
          <div class="col-md-6 badge badge-info" style="font-size: 1rem; white-space: normal;cursor: default;" v-on:click='downloadNepa()'>
            <p>
              Clique aqui para acessar a tabela nutricional brasileira que utilizei (TACO UNICAMP - NEPA)
            </p>
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
import Grafico01 from "@/components/Grafico01";
import BtnInput from "@/components/BtnInput";

export default {
  name: "Resultado",
  components: {
    Grafico01,
    BtnInput
  },
  props: [
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
    "taxaMetabolicaIndicada",
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
  data() {
    return {
      cores01: ["#41B883", "#E46651", "#FFFF00", "#00D8FF"],
      numeros01: [this.proteinas, this.carboidratos, this.gorduras, this.agua]
    };
  },
  methods:{
    redireciona(){
      window.open('https://supersaudeja.000webhostapp.com/');
    },
    downloadNepa(){
      window.open('static/nepa.xlsx');
    },
    downloadBase(){
      window.open('static/base.docx');
    }
  }
};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.main {
  margin-top: 3%;
}
.text-center {
  text-align: center !important;
}
.bottom-2 {
  margin-bottom: -2%;
}
.top-3 {
  padding-top: 3%;
}
.labelResultados {
  font-size: 1.4rem;
}
.numeroResultado {
  font-size: 1.6rem;
}
.titulo {
  font-family: Impact, Haettenschweiler, "Arial Narrow Bold", sans-serif;
  font-size: 2rem;
}
.margin-full {
  width: 90%;
  margin-left: 4%;
  margin-top: 2%;
  margin-bottom: 2%;
}
.textoAlimentos {
  font-size: 1.5rem;
}
#textoDowload{
  font-size: 1.7rem;
  margin-top: 10%;
}
.livro{
  background-color: rgb(248, 233, 215);
  margin-top: 3%;
  width: 99%;
}
#imgDownload{
  width: 50%;
}
.btnDownload{
  margin-top: -1%;
}

</style>
