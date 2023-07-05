<template>
  <div>
    <div class="Arrangement">
      <t-space>
        <t-radio-group default-value="1" class="check" size="large">
          <t-radio allow-uncheck value="1">1</t-radio>
          <t-radio allow-uncheck value="2">2</t-radio>
          <t-radio allow-uncheck value="3">3</t-radio>
          <t-radio allow-uncheck value="4">4</t-radio>
          <t-radio allow-uncheck value="5">5</t-radio>
          <t-radio allow-uncheck value="6">6</t-radio>
        </t-radio-group>
      </t-space>
    </div>
    <div class="Arrangement">
      <address-tool3></address-tool3>
    </div>
    <div class="Arrangement">
      <t-button size="large" class="send"> 发送 </t-button>
    </div>
  </div>
</template>
<script lang="ts" setup>
import { ref } from "vue";
import AddressTool3 from "@/components/address-tool3.vue";


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
.Arrangement {
  width: 460px;
  display: flex;
  flex-direction: column;
  margin-bottom: 150px;
}
.Arrangement_tool {
  display: flex;
  flex-direction: row;
}
</style>
