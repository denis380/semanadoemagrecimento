<template>
  <div>
    <div class="container">
      <h4 class="subtitle">{{ title || 'Teste' }}</h4>

      <span class="content">
          {{ texto || "..." }}
      </span>

    </div>
  </div>
</template>

<script>
export default {
  name: 'TextoCentral',
  props:[
    'title',
    'texto'
  ],
  data () {
    return {
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .subtitle{
    color: beige;
    font-size: 2.5rem;
  }
  .content{
    color: beige;
    font-size: 1.6rem;
    font-style: normal !important;
    font-family:Arial, Helvetica, sans-serif !important;

  }

</style>
