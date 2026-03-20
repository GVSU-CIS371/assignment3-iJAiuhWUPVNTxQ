<template>
  <div
    class="baseBeverage"
    :style="{ backgroundColor: props.base.color }"
  ></div>
</template>

<script setup lang="ts">
import { defineProps } from "vue";
import type { BaseBeverageType } from "../stores/beverage";

const props = defineProps<{
  base: BaseBeverageType;
}>();
</script>

<style scoped>
.baseBeverage {
  position: relative;
  width: 100%;
  height: 100%;
  bottom: 0;
  animation: pour-tea 2s;
  z-index: 300;
  border-radius: 0.05em 0.05em 2.2em 2.2em;
}

@keyframes pour-tea {
  from {
    height: 0;
  }
  to {
    height: 100%;
  }
}
</style>
