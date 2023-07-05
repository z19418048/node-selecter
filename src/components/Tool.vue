<template>
    <div v-for="(li, index) in inputList" :key="index">
      <t-input-group separate>
        <t-space direction="vertical" size="large">
          <t-input-adornment prepend="0x">
            <t-input
                v-for="li in inputList"
                :key="li.id"
                :disabled="li.disable"
                @keydown.tab="tab"
                @keydown.enter="enter"
                placeholder="请输入内容"
            ></t-input>
          </t-input-adornment>
        </t-space>
        <span :style="{ lineHeight: '32px' }">&nbsp;-&nbsp;</span>
      </t-input-group>
  </div>
</template>

<script lang="ts" setup>
import { ref } from "vue";
const inputList = ref([
  {
    id: 0,
    disable: false,
    input: "",
  },
]);
const tab = () => {
  inputList.value.map((el) => (el.disable = true));
  inputList.value.push({
    id: inputList.value.length,
    disable: false,
    input:''
  });

};
const enter = () => {
  inputList.value[inputList.value.length - 1].disable = true
}
// let total:object = {};
// const inputValue = ref(['']);
// const onEnter = (val:number,index:number) => {
//   total.push(val);
//   inputValue.value.push('');
//   console.log(total)
// }
</script>

<style scoped></style>
