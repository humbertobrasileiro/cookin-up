<script lang="ts">
export default {
  props: {
    texto: { type: String, required: true }
  }
}
</script>

<template>
  <button>
    <p>{{ texto }}</p>
  </button>
</template>