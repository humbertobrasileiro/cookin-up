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

    <BotaoPrincipal texto="Editar Lista" @click="$emit('selecionarIngredientes')" />
  </section>

</template>