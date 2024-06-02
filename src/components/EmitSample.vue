<!-- <template>
  <button type="button" v-on:click="handleUpdate" value="1">１</button>
  <button type="button" v-on:click="handleUpdate" value="2">２</button>
  <button type="button" v-on:click="handleUpdate" value="3">３</button>
</template>
<script setup lang="ts">
interface Emits {
  (event: "update", value: string): void;
}
const emit = defineEmits<Emits>();

const handleUpdate = (e: Event) => {
  emit("update", e.target.value);
};
</script> -->

<template>
  <button type="button" v-on:click="handleUpdate">乱数生成</button>
</template>
<script setup lang="ts">
interface Emits {
  (event: "updateRand", max: number): void;
}
const emit = defineEmits<Emits>();

const handleUpdate = () => {
  emit("updateRand", Math.round(Math.random() * 100));
};
</script>
