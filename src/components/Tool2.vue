<template>
  <div>
    <input type="text" v-model="inputValue" @keydown.tab="addInput">
    <input type="text" v-for="(input, index) in inputs" :key="index" v-model="input">
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputValue: '',
      inputs: []
    };
  },
  methods: {
    addInput() {
      this.inputs.push('');
      this.$nextTick(() => {
        const newInput = this.$el.querySelectorAll('input')[this.inputs.length];
        newInput.focus();
      });
    }
  }
};
</script>