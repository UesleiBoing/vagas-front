<template>
  <div>
    <keep-alive>
      <component :is="conteudo" />
    </keep-alive>
    
  </div>
  
</template>

<script>
import HomePadrao from '@/components/views/HomePadrao.vue';
import PublicarVaga from '@/components/views/PublicarVaga.vue';

export default {
  name: 'ConteudoPadrao',
  props: {
    conteudo : {
      type: String,
      required: true
    }
  },
  components: {
    HomePadrao,
    PublicarVaga
  }

  /* Todo componente passar por esses 4 evento, no processo de criação deles */
//  beforeCreate() {// Variaveis reativas ainda não disponiveis
//  console.log('Antes de criar', this.teste);
//  },
// created() {// A partir disso já pode usar reatividade
//  console.log('Criado', this.teste);
//  },
//  beforeMount() {
//    console.log('Antes de montar');
//  },
//  mounted() {
//    console.log('Montado');
//  },
  
  
  /* Atualização de estado do componente */
//  beforeUpdate() { /* Antes do componente ser atualizado*/
//    console.log('Antes de atualizar');  
//  },
//  updated() { /* Depois do componente ser atualizado */
//    console.log('Atualizado');
//  },
  
 // beforeUnmount(){ /* Antes de remover o componente */
 //   console.log('antes de desmontar');
 // },
 // unmounted(){ /* Depois de remover o componente */
 //   console.log('desmontado');
 // },
  /*
  errorCaptured() {
    console.log('Erro capturado');
  },
  renderTracked(){
    console.log('re-renderização rastreada');
  },
  renderTriggered(){
    console.log('Re-renderização adicionada');
  },
  activated(){
    console.log('Componente é ativado');
  },
  deactivated() {
    console.log('Componente é desativado');
  }*/
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style module>
.teste1{
  background-color: red;
}

#teste2 {
  background-color: pink;
}
</style>
