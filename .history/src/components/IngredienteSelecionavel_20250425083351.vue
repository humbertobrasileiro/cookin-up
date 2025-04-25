<script lang="ts">
import Tag from './Tag.vue';

export default {
  components: { Tag },
  props: {
    ingrediente: { type: String, required: true }
  },
  data() {
    return {
      selecionado: false
    }
  }
}
</script>

<template>
  <button>
    <Tag :texto="ingrediente" />
  </button>


</template>
