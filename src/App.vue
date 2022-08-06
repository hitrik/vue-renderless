<template>
  <div id="app">
    <RenderLess :options="options" />
  </div>
</template>

<script>
/*


      <template #default="{ isLoading, error, payload, triggerRequest }">
        <p class="content">
          {{ payload.value && JSON.stringify(payload.value) }}
        </p>
        <button @click="triggerRequest">Repeat Request</button>
      </template>

*/
import { defineComponent, reactive, ref } from 'vue';
import SkeletonComponent from './SkeletonComponent.vue';
import ErrorComponent from './ErrorComponent.vue';

import RenderLess from './components/RenderLess.vue';

export default defineComponent({
  name: 'App',
  components: {
    RenderLess,
  },

  setup() {
    const urlTodos = 'https://jsonplaceholder.typicode.com/todos';

    const delay = (ms = 1500) => new Promise((res) => setTimeout(res, ms));

    const requestTodos = () =>
      Promise.all([fetch(urlTodos), delay()]).then(([response]) =>
        response.json()
      );

    const options = reactive({
      request: requestTodos,
      immediate: true,
      skeletonComponent: SkeletonComponent,
      errorComponent: ErrorComponent,
    });
    /*
    <template #skeleton="{ isLoading, triggerRequest }">
      ...LOADING...
    </template>
    <template #error="{ error, triggerRequest }">
      ERROR OCCURRED: {{ error }}
    </template>

  */

    return {
      options,
    };
  },
});
</script>
