<template>
  <div class="post-code">
    <input maxlength="7" type="text" v-model="postCode" />
    <p>郵便番号：{{ hyphenCode }}</p>
    <p>日付：{{ displayDate() }}</p>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from "vue";

/* ①データを返す */
const postCode = ref("");

/* ②算出プロパティを定義する */
const hyphenCode = computed((): string => {
  return postCode.value.slice(0, 3) + "-" + postCode.value.slice(3, 7);
});

/* ③各メソッドを定義する */
const displayDate = (): any => {
  return new Date();
};
</script>
