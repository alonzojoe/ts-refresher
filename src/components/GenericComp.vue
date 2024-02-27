<template>
  <div class="box">
    <h1>Typescript Generic Props</h1>
    <p>Parent sent: {{ props.message }}</p>
  </div>
</template>

<script setup lang="ts">
const props = defineProps<{ message?: string }>();
</script>

<style scoped>
.box {
  height: 250px;
  width: 500px;
  border: 1px solid #fff;
  padding: 50px;
}
</style>
