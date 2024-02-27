<template>
  <div class="box">
    <h1>Typescript Generic Props</h1>
    <p>Parent sent: {{ message }}</p>
  </div>
</template>

<script setup lang="ts" generic="T extends string">
// const { message = "Parent did not send prop" } = defineProps<{
//   message: string;
// }>();
import { type GenericComp } from "./types";
defineProps<GenericComp<T>>();
</script>

<style scoped>
.box {
  height: 250px;
  width: 500px;
  border: 1px solid #fff;
  padding: 50px;
  border-radius: 15px;
}
</style>
