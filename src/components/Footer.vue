<template>
    <footer class="footer">
        <div class="small-box bg-gray">
            <div class="container">
                <div class="page-content page-container" id="page-content">
                    <div class="padding">
                        <div class="row container d-flex justify-content-center">
                            <div class="col-sm-6 padding-top-2"> 
                                <Social fundo='primary' logo='facebook' link='https://www.facebook.com/profile.php?id=100002366563743' />
                                <Espaco espacos='esquerda-4'/>
                                <Social fundo='dark' logo='instagram' link='https://www.instagram.com/diogorodrigueste/' />
                                <Espaco espacos='esquerda-4'/>
                                <Social fundo='info' logo='linkedin' link='' />
                                <Espaco espacos='esquerda-4'/>
                                <Social fundo='danger' logo='youtube' link='https://www.youtube.com/channel/UCJvGEBaZB1yKnyI5uGi1k1A' />
                                <Espaco espacos='esquerda-4'/>
                                <Social fundo='success' logo='spotify' link='https://open.spotify.com/show/19jQDLzQfFvhR981amCcCG' />
                                <Espaco espacos='esquerda-4'/>
                                <Social fundo='warning' logo='soundcloud' link='#' />
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="small-box-footer">
                    <a href="#"><small class="span-footer">SuperSaudeJá 2019</small></a>
               <Espaco espacos='direita-3'/>
               <a href="#"> <small class="span-footer">Privacidade</small></a>
               <Espaco espacos='direita-3'/>
               <a href="#"><small class="span-footer">Termos de uso</small></a>
            </div>
            
        </div>
</footer>
</template>

<script>
import Social from '@/components/Social'
import Espaco from '@/components/Espaco'

export default {
  name: 'Footer',
  components:{
      Social,
      Espaco
  },
  props:[
    
  ],
  data () {
    return {
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .small-box-footer{
        padding-bottom: 1%;
    }
    .container{
        padding-bottom: 2%;
    }
    .padding-top-2{
        padding-top: 2%;
    }
    .span-footer{
        color: beige;
    }
    .footer{
        margin-top:4%;
    }
</style>
