<template>
  <Calculator />
</template>

<script lang="ts">
  import { defineComponent } from 'vue';
  import Calculator from './components/calculator/Calculator.vue';

  export default defineComponent({
    name: 'App',
    components: { Calculator },
  });
</script>
