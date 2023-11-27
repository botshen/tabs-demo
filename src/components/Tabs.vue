<template>
  <div class="tabs">
    <ol class="tabs_nav">
      <li
        v-for="tab in tabs"
        :key="tab.props?.name"
        :class="{ selected: tab.props?.name === selected }"
        @click="updateSelected(tab.props?.name)"
      >
        {{ tab.props?.name }}
      </li>
    </ol>
    <div>
      {{ tabs.find }}
    </div>
  </div>
</template>

<script setup>
import { ref, useSlots } from "vue";
const slots = useSlots();
const props = defineProps({
  selected: String,
  onUpdateSelected: Function,
});
const selected = ref(props.selected);
const updateSelected = (name) => {
  if (props.onUpdateSelected) {
    props.onUpdateSelected(name);
  } else {
    selected.value = name;
  }
};

const tabs = slots.default?.() || [];
console.log(
  "%c [ tabs ]-38",
  "font-size:13px; background:pink; color:#bf2c9f;",
  tabs
);
</script>

<style scoped lang="scss">
/* Add your styles here */
.tabs {
  &_nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    text-align: center;
    color: red;

    > li {
      flex-grow: 1;
      flex-shrink: 0;
      padding: 12px 0;
      background: yellow;
      &.selected {
        background: green;
      }
    }
  }
}
</style>
