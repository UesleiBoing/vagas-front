<template>
  <div class="container py-4">
    <div class="row">
      <div class="col">
        <pesquisar-vaga></pesquisar-vaga>
      </div>
    </div>

    <!--
    <h2>Template customizado</h2>
    <lista-vagas>
      <template v-slot:titulo="slotProps">
        {{slotProps.dadosTitulo.titulo}}
        <hr>
      </template>
      <template v-slot:default="slotProps">
        {{slotProps}}
        <hr>
      </template>
      <template v-slot:rodape="slotProps">
        {{slotProps.dadosRodape.titulo}}
      </template>
      
    </lista-vagas>

    <br><br>
    <h2>Template padrão</h2>
    -->

    <lista-vagas></lista-vagas>

    <div class="row mt-5">
      <div class="col-4">
        indicador-padrao titulo="Vagas abertas" indicador="100" bg="bg-info" color="text-white"></indicador-padrao>
      </div>

      <div class="col-4">
        <indicador-padrao titulo="Profissionais Cadastrados" indicador="254" bg="bg-info" color="text-white"></indicador-padrao>
      </div>

      <div class="col-4">
        <indicador-padrao titulo="Visitantes online" :indicador="usuariosOnline" bg="bg-light" color="text-dark"></indicador-padrao>
      </div>
    </div>

  </div>
  
</template>

<script>
import IndicadorPadrao from '@/components/comuns/IndicadorPadrao.vue'
import ListaVagas from '@/components/comuns/ListaVagas.vue'
import PesquisarVaga from '@/components/comuns/PesquisarVaga.vue'

export default {
  name: 'HomePadrao',
  data: () => ({
    usuariosOnline: 0
  }),
  components: {
    IndicadorPadrao,
    ListaVagas,
    PesquisarVaga
  },
  methods: {
    getUsuariosOnline() {
      this.usuariosOnline = Math.floor(Math.random() * 101);
    }
  },
  created() {
    setInterval(this.getUsuariosOnline, 1000);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
