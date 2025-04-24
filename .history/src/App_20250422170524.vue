<template>
  <Banner />
</template>

<script lang="ts">
import { defineComponent({
  components: { Bannner }
})} from 'vue';

import Banner from './components/Banner.vue';

export default {
  components: { Banner }
};
</script>