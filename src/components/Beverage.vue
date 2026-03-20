<template>
  <Mug>
    <Cold v-if="isIced" />
    <Hot v-else />
    <Contents>
      <template #top>
        <!-- Creamer on top of everything when not 'No Cream' -->
        <Creamer v-if="creamer.name !== 'No Cream'" :creamer="creamer" />
      </template>

      <template #mid>
        <!-- Syrup layer only when not 'No Syrup' -->
        <Syrup v-if="syrup.name !== 'No Syrup'" :syrup="syrup" />
      </template>

      <template #bottom>
        <!-- Base beverage is always present -->
        <Base :base="base" />
      </template>
    </Contents>
  </Mug>
</template>

<script setup lang="ts">
import { computed } from "vue";
import Mug from "./Mug.vue";
import Contents from "./Contents.vue";
import Hot from "./Hot.vue";
import Cold from "./Cold.vue";
import Base from "./Base.vue";
import Creamer from "./Creamer.vue";
import Syrup from "./Syrup.vue";
import {
  bases,
  creamers,
  syrups,
  type BaseBeverageType,
  type CreamerType,
  type SyrupType,
} from "../stores/beverage";

type Props = {
  isIced: boolean;
  baseId: string;
  creamerId: string;
  syrupId: string;
};

const props = defineProps<Props>();

const base = computed<BaseBeverageType>(() => {
  return bases.value.find((b) => b.id === props.baseId) || bases.value[0];
});

const creamer = computed<CreamerType>(() => {
  return creamers.value.find((c) => c.id === props.creamerId) || creamers.value[0];
});

const syrup = computed<SyrupType>(() => {
  return syrups.value.find((s) => s.id === props.syrupId) || syrups.value[0];
});
</script>
