<script lang="ts">
export default {
  props: {
    texto: { type: String, requered: true }
  }
}
</script>

<template>
  <button>
    <p>{{ texto }}</p>
  </button>
</template>