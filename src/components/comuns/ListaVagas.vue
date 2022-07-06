<template>
    <div >
        <!--
        <slot name="titulo" :dadosTitulo="{titulo : 'Título Lista', nroVagas: 15}">
            <p>Título da lista de vagas</p>
        </slot>
        -->

        <slot :vagas="vagas">
            <div class="row mt-5" v-for="(vaga, index) in vagas" :key="index">
                <div class="col">
                    <vaga-padrao v-bind="vaga" />
                </div>
            </div>
        </slot>
        
        <!--
        <slot name="rodape" :dadosRodape="{ titulo: 'Rodapé lista', paginacao: {nroPaginas: 10, paginaAtual: 5}}">
            <p>O rodapé da lista de vagas</p>
        </slot>
        -->
    </div>
</template>
<script>
import VagaPadrao from '@/components/comuns/VagaPadrao.vue';
export default {
    name : 'ListaVagas',
    data : () => ({
        vagas: []
    }),
    components: {
        VagaPadrao
    },
    mounted() {
        this.emitter.on('filtrarVagas', vaga => {
          const vagas = JSON.parse(localStorage.getItem('vagas'));
          this.vagas = vagas.filter(registro => registro.titulo.toLowerCase().includes(vaga.titulo.toLowerCase()));

        });
    },
    activated() {
        this.vagas = JSON.parse(localStorage.getItem('vagas'));
    }
}
</script>
