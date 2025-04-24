<script lang="ts">
import type { PropType } from 'vue';
import Tag from './Tag.vue';

export default {
  props: {
    ingredientes: { type: Object as PropType<string[]>, required: true }
  },
  components: { Tag }
}
</script>

<template>
  <ul class="ingredientes-sua-lista">
    <li v-for="ingrediente in ingredientes" :key="ingrediente">
      <Tag :texto="ingrediente" ativa />
    </li>
  </ul>
</template>

<style scoped></style>