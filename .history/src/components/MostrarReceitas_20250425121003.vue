<script lang="ts">
import { obterReceitas } from '@/http/index';
import type IReceita from '@/interfaces/IReceita';

export default {
  data() {
    return {
      receitas: [] as IReceita[]
    }
  },
  async created() {
    this.receitas = await obterReceitas();
  },
  emits: ['selecionarIngredientes']
}
</script>

<template>
  <section class="mostrar-receitas">
    <h1 class="cabecalho titulo-receitas">Receitas</h1>
    <h2>Resultados encontrados:</h2>

    <p class="paragrafo">
      Veja as opções de receitas que encontramos com os ingredientes que você tem por aí!
    </p>

    <ul class="categorias">
      <li v-for="receita in receitas" :key="receita.nome">
        <CardCategoria :categoria="receita" />
      </li>
    </ul>

    <BotaoPrincipal texto="Editar Lista" @click="$emit('selecionarIngredientes')" />
  </section>

</template>