<template>
  <div class="box">
    <p>会員名：{{ name }}</p>
    <p>会員ID：{{ id }}</p>
    <p>保有ポイント：{{ points }}</p>
    <button v-on:click="pointUp">UP</button>
    <button v-on:click="pointDown">DOWN</button>
  </div>
</template>
<script setup lang="ts">
interface Props {
  id: number;
  name: string;
  points: number;
}

interface Emits {
  (event: "incrementPoint", id: number): void;
}

const props = defineProps<Props>();

const emit = defineEmits<Emits>();

const pointUp = (): void => {
  emit("incrementPoint", props.id);
};

const pointDown = (): void => {
  emit("decrementPoint", props.id);
};
</script>
<style scoped>
.box {
  border: 1px solid;
  margin: 10px;
  padding: 10px;
}
</style>
