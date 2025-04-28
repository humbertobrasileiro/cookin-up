<script lang="ts">
import type IReceita from '@/interfaces/IReceita';
import type { PropType } from 'vue';
export default {
  props: {
    receita: { type: Object as PropType<IReceita>, required: true }
  },
  components: {},
  emits: []
}
</script>

<template>
  <article class="receita">
    <header class="receita__cabecalho">
      <img :src="`/imagens/receitas/${receita.imagem}`" :alt="receita.nome" class="receita__imagem">
      <h2 class="paragrafo-lg receita__nome">{{ receita.nome }}</h2>
    </header>

    <ul class="receita__ingredientes">
      <li v-for="ingrediente in receita.ingredientes" :key="ingrediente">
        {{ ingrediente }}
      </li>
    </ul>
  </article>

</template>