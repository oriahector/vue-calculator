<template>
  <div class="calculator">
    <div class="calculator__output">{{ screenValue }}</div>
    <div class="calculator__button" @click="clickButton('1')">1</div>
    <div class="calculator__button" @click="clickButton('2')">2</div>
    <div class="calculator__button" @click="clickButton('3')">3</div>
    <div class="calculator__button orange" @click="clickButton('/')">÷</div>
    <div class="calculator__button" @click="clickButton('4')">4</div>
    <div class="calculator__button" @click="clickButton('5')">5</div>
    <div class="calculator__button" @click="clickButton('6')">6</div>
    <div class="calculator__button orange" @click="clickButton('*')">x</div>
    <div class="calculator__button" @click="clickButton('7')">7</div>
    <div class="calculator__button" @click="clickButton('8')">8</div>
    <div class="calculator__button" @click="clickButton('9')">9</div>
    <div class="calculator__button orange" @click="clickButton('-')">-</div>
    <div class="calculator__button" @click="clickButton('0')">0</div>
    <div class="calculator__button orange" @click="clickButton('C')">C</div>
    <div class="calculator__button orange" @click="clickButton('=')">=</div>
    <div class="calculator__button orange" @click="clickButton('+')">+</div>
  </div>
</template>

<script lang="ts" setup>
  /* imports */

  import { ref, computed } from 'vue';
  /* access var */
  const log = ref('');

  /* Computed */
  const screenValue = computed(() => {
    if (log.value == '') return 0;
    else return log.value;
  });

  /* Methods */
  const clickButton = (e: any) => {
    if (e == 'C') {
      clear();
    } else if (e == '=') {
      log.value = eval(log.value);
    } else {
      log.value = log.value + e;
    }
  };

  const clear = () => {
    log.value = '';
  };
</script>

<style scoped lang="scss" src="./Calculator.scss"></style>
