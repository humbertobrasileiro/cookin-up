<script lang="ts">
import { obterReceitas } from '@/http/index';
import type IReceita from '@/interfaces/IReceita';
import CardReceita from './CardReceita.vue';
import BotaoPrincipal from './BotaoPrincipal.vue';

export default {
  data() {
    return {
      receitasEncontradas: [] as IReceita[]
    }
  },
  async created() {
    const receitas = await obterReceitas();
    this.receitasEncontradas = receitas.slice(0, 8);
  },
  components: { BotaoPrincipal, CardReceita },
  emits: ['editarReceitas']
}
</script>

<template>
  <section class="mostrar-receitas">
    <h1 class="cabecalho titulo-receitas">Receitas</h1>

    <p class="paragrafo-lg resultados-encontrados">
      Resultados encontrados: {{ receitasEncontradas.length }}
    </p>

    <p class="paragrafo">
      Veja as opções de receitas que encontramos com os ingredientes que você tem por aí!
    </p>

    <ul class="receitas">
      <li v-for="receita in receitasEncontradas" :key="receita.nome">
        <CardReceita :receita="receita" />
      </li>
    </ul>

    <BotaoPrincipal texto="Editar Lista" @click="$emit('selecionarIngredientes')" />
  </section>

</template>

<style scoped>
.mostrar-receitas {
  width: 1200px;
  height: 628px;
}

.receitas {
  display: flex;
  flex-flow: wrap;
  gap: 10px;
}
</style>