<template>
  <div v-if="props.creamer.name !== 'No Cream'" class="froth" :style="creamStyle">
    <div v-for="i in 5" :key="i" class="foam"></div>
  </div>
</template>

<script setup lang="ts">
import { defineProps, computed } from "vue";
import type { CreamerType } from "../stores/beverage";

const props = defineProps<{
  creamer: CreamerType;
}>();

const creamStyle = computed(() => ({
  backgroundColor: props.creamer.color,
}));
</script>

<style lang="scss" scoped>
.froth {
  overflow: visible;
  transform: translateY(400%);
  position: relative;
  height: 20%;
  width: 100%;
  animation: pour-tea 2s 2s forwards;
}

.foam {
  display: block;
  background: #e4e0d2;
  border-radius: 30px;
  height: 40px;
  width: 40px;
  position: absolute;
}

.foam:nth-child(1) {
  top: 0px;
  left: -3px;
}

.foam:nth-child(2) {
  top: 0px;
  left: 55px;
}

.foam:nth-child(3) {
  width: 30px;
  height: 30px;
  border-radius: 40px;
  top: 3px;
  left: 30px;
}

.foam:nth-child(4) {
  width: 30px;
  height: 30px;
  border-radius: 45px;
  top: 5px;
  right: -2px;
}

.foam:nth-child(5) {
  top: 2px;
  right: 10px;
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
