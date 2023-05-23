<script setup lang="ts">
import { ref } from 'vue';

interface UseCounterOptions {
  min?: number;
  max?: number;
}

/**
 * Implement the composable function
 * Make sure the function works correctly
 */
function useCounter(initialValue = 0, options: UseCounterOptions = {}) {
  const { min, max } = options;
  const count = ref(initialValue);

  function inc() {
    count.value === max ? count.value : count.value++;
  }

  function dec() {
    count.value === min ? count.value : count.value--;
  }

  function reset() {
    count.value = initialValue;
  }

  return {
    count,
    inc,
    dec,
    reset,
  };
}

const { count, inc, dec, reset } = useCounter(0, { min: 0, max: 10 });
</script>

<template>
  <p>Count: {{ count }}</p>
  <button @click="inc">inc</button>
  <button @click="dec">dec</button>
  <button @click="reset">reset</button>
</template>
