<template>
  <div>
    <div class="container">
    <div><img src="static/img/cabecalho_termometro.png" alt="S2já" class="img-fluid logo responsive"></div>
  </div>
  </div>
</template>

<script>
export default {
  name: 'CabecalhoPrincipal',
  data () {
    return {
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.cabecalho {
  font-weight: normal;
  font-family: Impact;
  color: azure;
  font-size: 5rem;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.logo{
  width: 60%;
  margin-bottom: 5%;
  ;
}

</style>
