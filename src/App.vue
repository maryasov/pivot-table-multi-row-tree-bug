<template>
  <div id="app">
    <PivotTableTree />
  </div>
</template>

<script setup>
import { ref } from "vue";
import PivotTableTree from "./components/PivotTableTree.vue";
</script>

<style>
#app {
  display: flex;
}
</style>
