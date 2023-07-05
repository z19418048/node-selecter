<template>
  <div>
    <input v-for="(input, index) in inputs" :ref="inputRefs[index]" v-model="input" type="text" @keydown.enter="focusNextInput(index)">
  </div>
</template>

<script>
import { ref, onUpdated } from 'vue';

export default {
  setup() {
    const inputs = ref(['']);
    const inputRefs = ref([]);

    const focusNextInput = (index) => {
      const nextIndex = index + 1;
      if (nextIndex >= inputs.value.length) {
        inputs.value.push('');
        // 通过调用 nextTick 确保 inputRefs 已更新
        onUpdated(() => {
          inputRefs.value[nextIndex].focus();
        });
      } else {
        inputRefs.value[nextIndex].focus();
      }
    };

    return {
      inputs,
      inputRefs,
      focusNextInput,
    };
  },
};
</script>