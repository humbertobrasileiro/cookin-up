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
</template>