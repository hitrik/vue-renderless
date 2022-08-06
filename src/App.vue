<template>
  <div id="app">
    <img alt="Vue logo" src="https://vuejs.org/images/logo.png" />
    <RenderLess :options="options">
      <template #default="{ isLoading, error, payload, triggerRequest }">
        <p class="content">
          {{ payload.value && JSON.stringify(payload.value) }}
        </p>
        <button @click="triggerRequest">Repeat Request</button>
      </template>
    </RenderLess>
  </div>
</template>

<script>
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
      SkeletonComponent,
      ErrorComponent,
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
