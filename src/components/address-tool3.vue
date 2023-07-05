<template>
  <div
    style="display: flex; flex-direction: row"
    v-for="(outsideList, index) in inputList"
    :key="index"
  >
    <div style="display: flex">
      <div v-for="(li, liIndex) in outsideList" :key="liIndex">
        <input type="text" class="fixBar" disabled="false" placeholder="0x" />
        <input
          :id="li.id"
          :ref="li.id"
          :class="li.class"
          type="text"
          @keydown.tab="tab"
          @keydown.enter="enter"
          @keydown.shift="shift"
          :disabled="li.disable"
          v-model="li.input"
          :placeholder="li.tips"
        />
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import {onMounted, onUpdated, ref} from "vue";
const inputList = ref([
  [
    {
      id: "column" + 0 + "row" + 0,
      disable: false,
      input: "",
      outSideStyle: "content-tab",
      class: "inputStyle",
      tips: "请输入数字",
    },
  ],
]);
const columnValue = ref(0);
const rowValue = ref(0);

//新增行方法
const addRowValue = (columnValue: number, rowValue: number) => {
  inputList.value[columnValue].map((el) => (el.disable = true));
  inputList.value[columnValue].push({
    id: "column" + columnValue + "row" + rowValue,
    disable: false,
    input: "",
    outSideStyle: "",
    class: "inputStyle",
    tips: "请输入数字",
  });
}
onMounted(() => {
  document
      .getElementById(`${inputList.value[columnValue.value][rowValue.value].id}`)!
      .focus();
})
onUpdated(() => {
  document
      .getElementById(`${inputList.value[columnValue.value][rowValue.value].id}`)!
      .focus();
  console.log(columnValue.value)
  console.log(rowValue.value)
});
// console.log(inputList.value[inputList.value.length - 1][0].id);
// 新增列的方法
const addColumnValue = (columnValue: number, rowValue: number) => {
  let getInputListValue = inputList.value[columnValue];
  if (getInputListValue == undefined) {
    inputList.value.push([
      {
        id: "column" + columnValue + "row" + rowValue,
        disable: false,
        input: "",
        outSideStyle: "",
        class: "inputStyle",
        tips: "请输入数字",
      },
    ]);
  } else {
    getInputListValue.map((el) => (el.disable = true));
    inputList.value.push([
      {
        id: "column" + columnValue + "row" + rowValue,
        disable: false,
        input: "",
        outSideStyle: "",
        class: "inputStyle",
        tips: "请输入数字",
      },
    ]);
  }
};
const tab = () => {
  rowValue.value = rowValue.value + 1;
  addRowValue(columnValue.value, rowValue.value);
};
const enter = () => {
  const inputListLength = ref(inputList.value[columnValue.value].length - 1);
  inputList.value[columnValue.value][inputListLength.value].disable = true;
  if (rowValue.value != 0) {
    rowValue.value = 0;
  }
  columnValue.value = columnValue.value + 1;
  addColumnValue(columnValue.value, rowValue.value);
  // console.log(inputList.value[inputList.value.length - 1][0].id);
};
// TODO
const shift = () => {
  if (rowValue.value == 0 && columnValue.value == 0) {
    // 初始化数据
    columnValue.value = 0
    rowValue.value = 0
  // 保证第一行第一列的元素不会被删除
  }else if (rowValue.value == 0){
    // 一般情况下且当元素只留下一个的时候
    inputList.value.splice(columnValue.value)
    columnValue.value = columnValue.value - 1
    rowValue.value = inputList.value[columnValue.value].length - 1
    inputList.value[columnValue.value][rowValue.value].disable = false
  } else {
    // 平常情况
    inputList.value[columnValue.value].pop()
    rowValue.value = rowValue.value - 1
    inputList.value[columnValue.value][rowValue.value].disable = false
  }
  console.log(inputList.value)
  // console.log(rowValue.value)
};
</script>

<style scoped>
.inputStyle {
  width: 130px;
  height: 30px;
}
.fixBar {
  width: 22px;
  height: 30px;
}
/*变换时的样式*/
.content-tab {
  margin-top: 200px;
  display: flex;
}
.enter {
  display: flex;
  flex-direction: column;
}
</style>
