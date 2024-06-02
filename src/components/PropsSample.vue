<template>
  <section>
    <h1>{{ title }}</h1>
    <p>{{ description }}</p>
  </section>
</template>
<script setup lang="ts">
/* ここに適切な処理を記述 */
interface Props {
  title: string;
  description: string;
}
const props = defineProps<Props>();
</script>
