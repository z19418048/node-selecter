<template>
  <div class="content">
      <div style="display: inline-block">
        <input type="text" class="fixBar" disabled="false" placeholder="0x" />
        <input
          v-for="li in inputList"
          :key="li.id"
          :class="li.class"
          type="text"
          @keydown.tab="tab"
          @keydown.enter="enter"
          :disabled="li.disable"
          v-model="li.input"
          :placeholder="li.tips"
        />
      </div>
    <div style="display: inline-block">
      <input type="text" class="fixBar" disabled="false" placeholder="0x" />
      <input
          v-for="li in inputList"
          :key="li.id"
          :class="li.class"
          type="text"
          @keydown.tab="tab"
          @keydown.enter="enter"
          :disabled="li.disable"
          v-model="li.input"
          :placeholder="li.tips"
      />
    </div>
    <div>
      <input type="text" class="fixBar" disabled="false" placeholder="0x" />
      <input
          v-for="li in inputList"
          :key="li.id"
          :class="li.class"
          type="text"
          @keydown.tab="tab"
          @keydown.enter="enter"
          :disabled="li.disable"
          v-model="li.input"
          :placeholder="li.tips"
      />
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref } from "vue";
const total = ref([])
const inputList = ref([
  {
    id: 0,
    disable: false,
    input: "",
    class: "inputStyle",
    tips: "请输入数字",
  },
]);
const tab = () => {
  inputList.value.map((el) => (el.disable = true));
  inputList.value.push({
    id: inputList.value.length,
    disable: true,
    input: "",
    class: "fixBar",
    tips: "0x",
  });
  inputList.value.push({
    id: inputList.value.length,
    disable: false,
    input: "",
    class: "inputStyle",
    tips: "请输入数字",
  });
};
const enter = () => {
  inputList.value.map((el) => (el.disable = true));
  inputList.value.push({
    id: inputList.value.length,
    disable: true,
    input: "",
    class: "fixBar__enter",
    tips: "0x",
  });
  inputList.value.push({
    id: inputList.value.length,
    disable: false,
    input: "",
    class: "inputStyle__enter",
    tips: "请输入数字",
  });
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
  width: 130px;
  height: 30px;
}
.fixBar {
  width: 22px;
  height: 30px;
}
.fixBar__enter {
  width: 22px;
  height: 30px;
  display: block;
}
.inputStyle__enter {
  width: 130px;
  height: 30px;
}
.tab {
  display: flex;
}
.enter {
  display: flex;
  flex-direction: column;
}
</style>
