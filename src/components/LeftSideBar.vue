<template>
  <div class="side-bar">
    <Logo></Logo>
    <Tabs></Tabs>
  </div>
</template>

<script>
import Logo from "@/components/sidebarComponents/Logo";
import Tabs from "@/components/sidebarComponents/Tabs";

export default {
  name: "LeftSideBar",
  components: {
    Logo,
    Tabs
  }
}
</script>

<style scoped>
  .side-bar {
    display: flex;
    flex-direction: column;
  }
</style>