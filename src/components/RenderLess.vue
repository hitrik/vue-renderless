<script>
import {
  defineComponent,
  ref,
  reactive,
  toRefs,
  onMounted,
  watch,
  h,
} from 'vue';

export default defineComponent({
  name: 'RenderLess',

  /*
    options schema
    {
      requestWorker: Function, // function makes async request to the server for payload
      immediate?: boolean, // invoke requestWorker on mounted automatically
      skeletonComponent?: VueInstance, // component used to show a spinner/loader
      errorComponent?: VueInstance, // component used to show an error
    }
    */

  props: {
    options: {
      type: Object,
      required: true,
    },
  },

  setup(props, ctx) {
    // const data = reactive({
    //   payload: null,
    //   isLoading: false,
    //   error: null,
    // });

    // const { request, immediate, errorComponent, skeletonComponent } =
    //   props.options;

    // const startRequest = async () => {
    //   try {
    //     data.error = null;
    //     data.isLoading = true;
    //     const response = await request.value();
    //     data.payload = response;
    //   } catch (error) {
    //     console.log(error);
    //     data.error = error;
    //   } finally {
    //     data.isLoading = false;
    //   }
    // };

    // const trigger = ref(false);

    // const triggerRequest = () => (trigger.value = !trigger.value);

    // watch(trigger, startRequest);

    // onMounted(() => {
    //   immediate.value && startRequest();
    // });

    // const fProps = { ...toRefs(data), triggerRequest };
    // const renderValue = ref(h(skeletonComponent, fProps));

    // watch(data, (changed) => {
    //   console.log('changed', changed);

    //   if (data.error) {
    //     renderValue.value = () => h(errorComponent, fProps);
    //     return;
    //   }

    //   if (data.isLoading) {
    //     renderValue.value = () => h(skeletonComponent, fProps);
    //     return;
    //   }

    //   renderValue.value = () => ctx.slots.default?.(fProps);
    // });

    return () => h('div', null, ['github']);
  },
});
</script>
