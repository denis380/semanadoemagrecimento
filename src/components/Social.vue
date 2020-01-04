<template>
    <span>
        <a :href="link" type="button" :class="'btn btn-rounded btn-icon btn-'+fundo" target="blank"> <i :class="'fab fa-'+logo"></i> </a> 
    </span>
</template>

<script>
export default {
  name: 'Social',
  components:{
      
  },
  props:[
    "fundo",
    "logo",
    "link"
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
</style>
