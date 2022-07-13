<template>
    <div :class="estiloAlerta" role="alert">
        <slot name="titulo">
            <h3>Titulo da mensagem de feedback</h3>
        </slot>
        <hr>
        <slot><p>Padrão do feedback</p></slot>
      </div>
</template>
<script>
export 2default {
    name: 'AlertaPadrao',
    props: { tipo: String },
    computed: {
        estiloAlerta() {
            switch(this.tipo) {
                case 'erro': return 'alert alert-danger';
                case 'sucesso': return 'alert alert-success';
                default: return 'alert alert-success';
            }
        }
    }
}
</script>
