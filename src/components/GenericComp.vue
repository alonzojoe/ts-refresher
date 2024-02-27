<template>
  <div class="box">
    <h1>Typescript Generic Props</h1>
    <p>Parent sent: {{ props.message }}</p>
  </div>
</template>

<script setup lang="ts" generic="T extends string">
// const props = defineProps<{
//   message: string;
// }>();
// const { message = "Parent did not send prop" } = defineProps<{
//   message: string;
// }>();
// import { type GenericComp } from "./types";
// defineProps<GenericComp<T>>();
// import type { PropType } from "vue";

// export interface Props {
//   message: string;
// }

// defineProps({
//   message: Object as PropType<Props>,
// });

const props = withDefaults(defineProps<{ message?: string }>(), {
  message: "default message when parent did not send me prop :(",
});

// const emit = defineEmits<{
//   //When passing state type to parent
//   (e: "change", id: number): void;
//   (e: "update", value: string): void;
// }>();

// const emit = defineEmits<{
//   // When triggering an action and no state is passed to the parent
//   (e: "update"): void;
//   (e: "change"): void;
// }>();

// newstyle in vue3
const emit = defineEmits<{
  change: [id: string];
  update: [value: string];
}>();
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
