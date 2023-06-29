<template>
  <div>
    <div class="Arrangement">
      <t-radio-group default-value="1" @change="onChange" class="check" size="large">
        <t-radio allow-uncheck value="1">1</t-radio>
        <t-radio allow-uncheck value="2">2</t-radio>
        <t-radio allow-uncheck value="3">3</t-radio>
        <t-radio allow-uncheck value="4">4</t-radio>
        <t-radio allow-uncheck value="5">5</t-radio>
        <t-radio allow-uncheck value="6">6</t-radio>
      </t-radio-group>
    </div>
    <div class="Arrangement">
      <tools></tools>
    </div>
    <div class="Arrangement">
      <t-button size="large" class="send"> 发送 </t-button>
    </div>
  </div>
</template>

<script setup>
import Tools from "@/components/Tools.vue";
</script>

<style scoped>
.check {
  display: flex;
  margin-top: 100px;
}
.tool {
  display: flex;
  margin-top: 100px;
}
.send {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 200px;
}
.Arrangement{
  width: 480px;
  display: flex;
  flex-direction: column;
  margin-bottom: 150px;
}
</style>
