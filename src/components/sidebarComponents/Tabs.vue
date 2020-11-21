<template>
  <div class="side-bar__tabs tabs">
    <Tab></Tab>
    <Tab></Tab>
  </div>
</template>

<script>
import Tab from "@/components/sidebarComponents/Tab";

export default {
  name: "Tabs",
  components: {
    Tab
  }
}
</script>

<style scoped>
  .side-bar__tabs {
    margin-top: 90px;
  }
</style>