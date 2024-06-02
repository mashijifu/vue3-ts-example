<template>
  <div class="post-code">
    <section>
      <ul>
        <PropsSample
          v-for="language in languageList"
          :key="language.id"
          :id="language.id"
          :name="language.name"
        />
      </ul>
    </section>
    <input maxlength="7" type="text" v-model="postCode" />
    <p>郵便番号：{{ hyphenCode }}</p>
    <p>日付：{{ displayDate() }}</p>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from "vue";
import PropsSample from "@/components/PropsSample.vue";

const postCode = ref("");
const languageList = [
  { id: 1, name: "PHP" },
  { id: 2, name: "Java" },
  { id: 3, name: "HTML" },
  { id: 4, name: "CSS" },
  { id: 5, name: "TypeScript" },
];

const hyphenCode = computed((): string => {
  return postCode.value.slice(0, 3) + "-" + postCode.value.slice(3, 7);
});

const displayDate = (): any => {
  return new Date();
};
</script>
