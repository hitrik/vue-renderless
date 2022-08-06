<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'ErrorComponent',
  props: {
    error: {
      type: [Object, String],
      required: true,
    },
  },
});
</script>

<template>
  <div>
    {{ error }}
  </div>
</template>
