<script setup>
import Tabs from "./components/Tabs.vue";
import Tab from "./components/Tab.vue";
import { ref } from "vue";
const activeName = ref("222");
const onUpdatedSelected = (tab) => {
  console.log(
    "%c [ tab ]-8",
    "font-size:13px; background:pink; color:#bf2c9f;",
    tab
  );
};
</script>

<template>
  <div>
    <Tabs v-model="activeName" @onUpdatedSelected="onUpdatedSelected">
      <Tab name="111"> aa323aa </Tab>
      <Tab name="222"> ba3232323aa </Tab>
      <Tab name="333"> 323 </Tab>
      <Tab name="444"> baa3232a </Tab>
    </Tabs>
  </div>
</template>
