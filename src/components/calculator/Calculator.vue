<template>
  <div class="calculator">
    <p
      class="calculator__output"
      :class="{ small: result.length > 9 || result.toString().length > 9 }"
    >
      {{ screenValue }}
    </p>
    <div @click="clickButton('1')">1</div>
    <div @click="clickButton('2')">2</div>
    <div @click="clickButton('3')">3</div>
    <div class="orange" @click="clickButton('/')">÷</div>
    <div @click="clickButton('4')">4</div>
    <div @click="clickButton('5')">5</div>
    <div @click="clickButton('6')">6</div>
    <div class="orange" @click="clickButton('*')">x</div>
    <div @click="clickButton('7')">7</div>
    <div @click="clickButton('8')">8</div>
    <div @click="clickButton('9')">9</div>
    <div class="orange" @click="clickButton('-')">-</div>
    <div @click="clickButton('0')">0</div>
    <div class="orange" @click="clickButton('C')">C</div>
    <div class="orange" @click="clickButton('=')">=</div>
    <div class="orange" @click="clickButton('+')">+</div>
  </div>
</template>

<script lang="ts" setup>
  /* imports */
  import { ref, computed } from 'vue';

  /* access var */
  const result = ref('');

  /* Computed */
  // inferred type: ComputedRef<number>
  // the value will be displayed in the output screen
  const screenValue = computed(() => {
    if (result.value == '') return 0;
    else return result.value;
  });

  /* Methods */
  const clickButton = (e: string) => {
    if (e == 'C') {
      clear();
    } else if (e == '=') {
      result.value = eval(result.value);
      // if clicked button is not '=' or C, concat the buttons clicked in the result const
    } else {
      result.value = result.value + e;
    }
  };

  // clear function
  const clear = () => {
    result.value = '';
  };
</script>

<style scoped lang="scss" src="./Calculator.scss"></style>
