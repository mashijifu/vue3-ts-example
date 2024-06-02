<template>
  <li>
    <p>{{ id }}</p>
    <p>{{ name }}</p>
  </li>
</template>
<script setup lang="ts">
/* ここに適切な処理を記述 */
interface Props {
  id: number;
  name: string;
}
const props = defineProps<Props>();
</script>
