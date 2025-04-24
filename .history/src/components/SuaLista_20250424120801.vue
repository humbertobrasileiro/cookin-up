<script lang="ts">
import type { PropType } from 'vue';
import Tag from './Tag.vue';

export default {
  props: {
    ingredientes: { type: Array as PropType<string[]>, required: true }
  },
  components: { Tag }
}
</script>

<template>
  <section>
    <span class="subtitulo-lg sua-lista-texto">
      Sua lista:
    </span>

    <ul class="ingredientes-sua-lista">
      <li v-for="ingrediente in ingredientes" :key="ingrediente">
        <Tag :texto="ingrediente" ativa />
      </li>
    </ul>

  </section>
</template>

<style scoped>
.sua-lista-texto {
  color: var(--coral, #F0633C);
  display: block;
  text-align: center;
  margin-bottom: 1.5rem;
}
</style>