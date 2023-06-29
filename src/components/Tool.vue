<template>
<div v-for="(value, index) in inputValue" :key="index">
  <t-input-group separate>
    <t-space direction="vertical" size="large">
      <t-input-adornment prepend="0x">
        <t-input v-model="inputValue" @enter="onEnter" placeholder="请输入内容"></t-input>
      </t-input-adornment>
    </t-space>
    <span :style="{ lineHeight: '32px' }">&nbsp;-&nbsp;</span>
  </t-input-group>

</div>
</template>

<script lang="ts" setup>
import {ref} from "vue";
let total:object = {};
const inputValue = ref(['']);
const onEnter = (val:number,index:number) => {
  total.push(val);
  inputValue.value.push('');
  console.log(total)
}
</script>

<style scoped>

</style>