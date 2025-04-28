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

}
</script>

<template>
  <section class="mostrar-receitas">

  </section>

</template>