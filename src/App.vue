<template>
  <div>
    <Beverage
      :isIced="currentTemp === 'Cold'"
      :base-id="currentBaseId"
      :creamer-id="currentCreamerId"
      :syrup-id="currentSyrupId"
    />

    <ul>
      <li>
        <template v-for="temp in temps" :key="temp">
          <label>
            <input
              type="radio"
              name="temperature"
              :id="`r${temp}`"
              :value="temp"
              v-model="currentTemp"
            />
            {{ temp }}
          </label>
        </template>
      </li>
    </ul>

    <div class="controls">
      <div class="control-group">
        <label>Base Beverage:</label>
        <select v-model="currentBaseId">
          <option v-for="base in bases" :key="base.id" :value="base.id">
            {{ base.name }}
          </option>
        </select>
      </div>

      <div class="control-group">
        <label>Creamer:</label>
        <select v-model="currentCreamerId">
          <option
            v-for="creamer in creamers"
            :key="creamer.id"
            :value="creamer.id"
          >
            {{ creamer.name }}
          </option>
        </select>
      </div>

      <div class="control-group">
        <label>Syrup:</label>
        <select v-model="currentSyrupId">
          <option v-for="syrup in syrups" :key="syrup.id" :value="syrup.id">
            {{ syrup.name }}
          </option>
        </select>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Beverage from "./components/Beverage.vue";
import {
  temps,
  currentTemp,
  bases,
  creamers,
  syrups,
} from "./stores/beverage";

const currentBaseId = ref(bases.value[0].id);
const currentCreamerId = ref(creamers.value[0].id);
const currentSyrupId = ref(syrups.value[0].id);
</script>

<style lang="scss">
body,
html {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: #6e4228;
  background: linear-gradient(to bottom, #6e4228 0%, #956f5a 100%);
}

ul {
  list-style: none;
  padding-left: 0;
}

.controls {
  margin-top: 16px;
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
}

.control-group {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

select {
  padding: 4px 6px;
  border-radius: 4px;
}
</style>
