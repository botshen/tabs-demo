<template>
  <div v-show="isActive">
    <slot></slot>
  </div>
</template>

<script setup>
import { inject, computed } from "vue";

const props = defineProps({
  name: {
    type: String,
    required: true,
  },
});

const activeName = inject("activeName");

const isActive = computed(() => props.name === activeName.value);
</script>
