<template>
  <div>Hook</div>
</template>

<script>
import { onBeforeMount, onBeforeUnmount, onMounted, onUnmounted } from "vue";
export default {
  beforeMount() {},
  mounted() {},
  beforeUnmount() {},
  unmounted() {},
  setup() {
    onBeforeMount(() => {
      console.log("onBeforeMount");
    });

    onMounted(() => {
      console.log("Mounted");
    });
    onBeforeUnmount(() => {
      console.log("onBeforeUnmounted");
    });
    onUnmounted(() => {
      console.log("Unmounted");
    });
  },
};
</script>
