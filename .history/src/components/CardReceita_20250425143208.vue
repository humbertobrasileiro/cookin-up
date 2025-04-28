<script lang="ts">
import type IReceita from '@/interfaces/IReceita';
import type { PropType } from 'vue';

export default {
  props: {
    receita: { type: Object as PropType<IReceita>, required: true }
  },
}
</script>

<template>
  <article class="receita">
    <header class="receita__cabecalho">
      <img :src="`/imagens/receitas/${receita.imagem}`" :alt="receita.nome" class="receita__imagem">
    </header>

    <section class="receita__corpo">
      <h2 class="paragrafo receita__nome">{{ receita.nome }}</h2>
    </section>
  </article>
</template>

<style scoped>
.receita__imagem {
  width: 282px;
  height: 150px;
}
</style>