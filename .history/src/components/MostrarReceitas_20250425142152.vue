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

    <div v-if="receitasEncontradas.length" class="receitas-wrapper">
      <p class="paragrafo-lg informacoes">
        Veja as opções de receitas que encontramos com os ingredientes que você tem por aí!
      </p>

      <ul class="receitas">
        <li v-for="receita in receitasEncontradas" :key="receita.nome">
          <CardReceita :receita="receita" />
        </li>
      </ul>
    </div>

    <div v-else class="receitas-nao-encontradas">
      <p class="paragrafo-lg receitas-nao-encontradas__info">
        Ops, não encontramos resultados para sua combinação. Vamos tentar de novo?
      </p>

      <img src="../assets/imagens/sem-receitas.png"
        alt="Desenho de um ovo quebrado. A gema tem um rosto com uma expressão triste.">
    </div>

    <BotaoPrincipal texto="Editar Lista" @click="$emit('editarReceitas')" />
  </section>

</template>

<style scoped>
.mostrar-receitas {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.receitas {
  display: flex;
  flex-flow: wrap;
  gap: 10px;
}
</style>