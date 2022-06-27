<template>
  <div>
    <vagas-favoritas></vagas-favoritas>
    <topo-padrao @navegar="componente = $event;"/>
    <alerta-padrao v-if="exibirAlerta" :tipo="alerta.tipo">
      <template v-slot:titulo>
        <h5> {{alerta.titulo}}</h5>
      </template>
      <p>{{alerta.descricao}}</p>

    </alerta-padrao>
    <conteudo-padrao v-if="visibilidade" :conteudo="componente"/>
  </div>
</template>

<script>
import AlertaPadrao from '@/components/comuns/AlertaPadrao.vue'
import ConteudoPadrao from '@/components/layouts/ConteudoPadrao.vue'
import TopoPadrao from '@/components/layouts/TopoPadrao.vue'
import VagasFavoritas from '@/components/comuns/VagasFavoritas.vue'

export default {
  name: 'App',
  data: () => ({
    visibilidade : true,
    componente: 'HomePadrao',
    exibirAlerta: false,
    alerta: {
      titulo : '',
      descricao : '',
      tipo: ''
    }
  }),
  components: {
    AlertaPadrao,
    ConteudoPadrao,
    TopoPadrao,
    VagasFavoritas
  },
  mounted(){
    this.emitter.on('alerta', (oParametro) => {
      this.alerta = oParametro;
      this.exibirAlerta = true;
      setTimeout(() => this.exibirAlerta = false, 4000);
    })
  }
}

</script>

<style scoped>
</style>
