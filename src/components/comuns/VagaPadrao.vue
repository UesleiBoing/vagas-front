<template>
    <div class="card">
        <div class="card-header bg-dark text-white">
            <div class="row">
                <div class="col d-flex justify-content-between">
                    <div>
                        {{titulo}}
                    </div>
                    <div>
                        <div class="form-check form-switch">
                            <input class="form-check-input" type="checkbox" v-model="favoritada">
                            <label class="form-check-label">Favoritar</label>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="card-body">
            <p>{{descricao}}</p>
        </div>
        <div class="card-footer">
            <small class="text-muted">Salário: R${{salario}} | Modalidade: {{getModalidade}} | Tipo: {{getTipo}} | Publicação: {{getPublicacao}}</small>
        </div>
    </div>
</template>
<script>
export default {
    name: 'VagaPadrao',
    data: () => ({
        favoritada : false
    }),
    watch: {
        favoritada(valorNovo) {
            if(valorNovo) {
                this.emitter.emit('favoritarVaga', this.titulo);
            } else {
                this.emitter.emit('desfavoritarVaga', this.titulo);
            }
        }
    },
   // props: ['titulo', 'descricaoVaga', 'salario', 'modalidade', 'tipo', 'publicacao'],
    props: {
        titulo: {
            type: String,
            required: true,
            validator(prop) {
                return prop.length < 6; //Invalido
              //  return true; //Valido
            }
        },
        descricao: {
            type: String,
            default: 'O Contratante não adicionou informações da vaga'
        },
        salario: {
            type: [Number, String],
            default() {
                return Math.floor(Math.random() * 10000);
            }
        },
        modalidade: {
            type: String,
            required: true
        },
        tipo: {
            type: String,
            required: true
        },
        publicacao: {
            type: String,
            required: true
        }
    },
    computed: {
        getModalidade(){
            switch(this.modalidade) {
                case '1': return 'Home Office';
                case '2': return 'Presencial';
            }
            return '';
        },
        getTipo(){
            switch(this.tipo) {
                case '1': return 'CLT';
                case '2': return 'PJ';
            }
            return '';
        },
        getPublicacao() {
            let dataPublicacao = new Date(this.publicacao);
            return dataPublicacao.toLocaleDateString('pt-BR');
        }
    }
}
</script>