<template>
  <div :class="estilo">
    <p>{{ titulo }}</p>
    <h2>{{ indicador }}</h2>
  </div>
</template>

<script>
export default {
  name: 'IndicadorPadrao', 
  props: ['titulo', 'indicador', 'bg', 'color'], /* Propriedades que o componente filho pode receber */
  computed: {
    estilo() {
      return `h-100 p-5 rounded-3 border ${this.bg} ${this.color}`;
    }
  }
}
</script>

<style>
</style>
