<template>
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
</script>
