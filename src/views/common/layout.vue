<template>
  <div>
    <t-layout class="page">
      <div class="component">
        <network-sidebar></network-sidebar>
      </div>
      <div class="component">
        <point-sidebar></point-sidebar>
      </div>
      <div class="component">
        <page-layout></page-layout>
      </div>
    </t-layout>
  </div>
</template>

<script setup>
import NetworkSidebar from "@/views/common/network-sidebar.vue";
import PointSidebar from "@/views/common/point-sidebar.vue";
import PageLayout from "@/views/common/page-layout.vue";
</script>

<style scoped>
.page {
  height: 100vh;
  display: grid;
  grid-template-columns: 1fr 3fr 4fr;
  grid-gap: 10px;
}
.component {
  display: flex;
}
</style>
