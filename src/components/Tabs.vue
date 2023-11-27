<template>
  <div>
    <div
      class="tab"
      v-for="tab in tabs"
      :key="tab?.name"
      @click="handleClick(tab.name)"
    >
      {{ tab?.name }}
    </div>
    <slot></slot>
  </div>
</template>

<script setup>
import { ref, provide, watch, onMounted, useSlots } from "vue";

const props = defineProps({
  modelValue: {
    type: String,
    default: "",
  },
});

const activeName = ref(props.modelValue);
provide("activeName", activeName);

watch(
  () => props.modelValue,
  (newVal) => {
    activeName.value = newVal;
  }
);

const emit = defineEmits(["update:modelValue", "onUpdatedSelected"]);

const handleClick = (tab) => {
  emit("onUpdatedSelected", tab);
  emit("update:modelValue", tab);
};

let tabs = ref([]);
const slots = useSlots();

onMounted(() => {
  tabs.value = slots.default()?.map((vnode) => vnode.props);
});
</script>

<style scoped>
.tab {
  display: inline-block;
  padding: 10px;
  margin: 0 10px;
}
</style>
