<template>
  <div>
    <input ref="inputRef" type="text" />
    <button @click="focusInput">聚焦输入框</button>
  </div>
</template>

<script>
import { ref, nextTick } from 'vue';

export default {
  setup() {
    const inputRef = ref(null);

    const focusInput = () => {
      nextTick(() => {
        inputRef.value.focus();
      });
    };

    return {
      inputRef,
      focusInput,
    };
  },
};
</script>