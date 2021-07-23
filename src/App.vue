<template>
  <router-view />
</template>
<script>
import { defineComponent } from "vue";
import { useQuasar } from 'quasar';

export default defineComponent({
  name: "App",
  mounted() {
    const $q = useQuasar()
    $q.dark.set(true);
  },
});
</script>
