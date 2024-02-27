<template>
  <div class="box">
    <h1>Typescript Generic Props</h1>
    <p>Parent sent: {{ props.message }}</p>
    <span>{{ year }}</span>
    <span>{{ book }}</span>
  </div>
</template>

<script setup lang="ts" generic="T extends string">
// import { ref, type Ref, onMounted } from "vue";
// const year: Ref<string | number> = ref(2024);
// const year = ref<number>();
// const year = ref<number>({} as unknown as number);

// onMounted(() => {
//   year.value = 2023;
// });

///------
import { reactive, Ref } from "vue";

interface Book {
  title: string;
}

const book: Ref<Book> = reactive({ title: "Titanic" });

///-------
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
  change: [id: string]; //bracket style notation
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
