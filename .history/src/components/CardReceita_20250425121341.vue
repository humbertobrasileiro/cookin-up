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
  <article class="categoria">
    <header class="categoria__cabecalho">
      <img :src="`/imagens/icones/categorias_ingredientes/${categoria.imagem}`" :alt="categoria.nome"
        class="categoria__imagem">
      <h2 class="paragrafo-lg categoria__nome">{{ categoria.nome }}</h2>
    </header>

    <ul class="categoria__ingredientes">
      <li v-for="ingrediente in categoria.ingredientes" :key="ingrediente">
        <IngredienteSelecionavel :ingrediente="ingrediente"
          @adicionar-ingrediente="$emit('adicionarIngrediente', $event)"
          @remover-ingrediente="$emit('removerIngrediente', $event)" />
      </li>
    </ul>
  </article>

</template>