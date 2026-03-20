<template>
  <div class="syrup" :style="syrupStyle" v-if="props.syrup.name !== 'No Syrup'"></div>
</template>

<script setup lang="ts">
import { defineProps, computed } from "vue";
import type { SyrupType } from "../stores/beverage";

const props = defineProps<{
  syrup: SyrupType;
}>();

const syrupStyle = computed(() => ({
  backgroundColor: props.syrup.color,
}));
</script>

<style lang="scss" scoped>
.syrup {
  transform: translateY(400%);
  position: relative;
  width: 100%;
  height: 20%;
  animation: pour-tea 2s 1s forwards;
  z-index: 2;
}

@keyframes pour-tea {
  from {
    height: 0;
  }
  to {
    height: 20%;
  }
}
</style>
