<template>
  <div>
    <input
        v-for="(input, index) in inputs"
        :key="index"
        ref="inputRefs"
        v-model="input"
        type="text"
        @keydown.enter="focusNextInput(index)"
    >
  </div>
</template>

<script>
import { ref, onMounted } from 'vue';

export default {
  setup() {
    const inputs = ref(['']);

    const focusNextInput = (index) => {
      const nextIndex = index + 1;
      if (nextIndex >= inputs.value.length) {
        inputs.value.push('');
      }
      nextTick(() => {
        inputRefs.value[nextIndex].focus();
      });
    };

    const inputRefs = ref([]);

    onMounted(() => {
      inputRefs.value[0].focus();
    });

    return {
      inputs,
      focusNextInput,
      inputRefs,
    };
  },
};
</script>