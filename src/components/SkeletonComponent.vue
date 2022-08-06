<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'SkeletonComponent',
  props: {
    isLoading: {
      type: Boolean,
      default: true,
    },
  },
});
</script>

<template>
  <div>
    Custom Skeleton Component

    <p>Loading content...</p>
  </div>
</template>

<style scoped>
p {
  color: tomato;
  font-size: 16px;
  text-transform: upercase;
}
</style>
