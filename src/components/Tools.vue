<template>
  <div class="content">
    <input type="text" v-for="li in inputList" :key="li.id" class="fixBar" disabled="false" placeholder="0x" />
    <input
      class="inputStyle"
      v-for="li in inputList"
      type="text"
      @keydown.tab="tab"
      :key="li.id"
      :disabled="li.disable"
    />
  </div>
</template>

<script lang="ts" setup>
import { ref } from "vue";
let total = [];
const inputList = ref([
  {
    id: 0,
    disable: false,
  },
]);
const tab = () => {
  inputList.value.map((el) => (el.disable = true));
  inputList.value.push({
    id: inputList.value.length,
    disable: false,
  });
  total.push(inputList.value);
};
</script>
<style scoped>
.content {
  margin-top: 200px;
}
.send {
  margin-top: 500px;
}
.inputStyle {
  width: 150px;
  height: 30px;
}
.fixBar {
  width: 22px;
  height: 30px;
}
</style>
