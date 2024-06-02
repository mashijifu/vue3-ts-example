<template>
  <div class="post-code">
    <section>
      <div>
        <h2>ポイント合計: {{ totalPoints }}</h2>
      </div>
      <div class="member">
        <OneMember
          v-for="[id, member] in memberList"
          v-bind:key="id"
          v-bind:id="id"
          v-bind:name="member.name"
          v-bind:points="member.points"
          v-on:incrementPoint="onIncrementPoint"
          v-on:decrementPoint="onDecrementPoint"
        />
      </div>
    </section>
    <section>
      <h1>Vue{{ version }}.xの学習</h1>
      <EmitSample v-on:update="updateVersion" />
    </section>
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
import EmitSample from "@/components/EmitSample.vue";
import OneMember from "@/components/OneMember.vue";

const postCode = ref("");
const version = ref("?");
const updateVersion = (value: string): void => {
  version.value = value;
};
const languageList = [
  { id: 1, name: "PHP" },
  { id: 2, name: "Java" },
  { id: 3, name: "HTML" },
  { id: 4, name: "CSS" },
  { id: 5, name: "TypeScript" },
];
const memberListInit = new Map<number, Member>();
memberListInit.set(1, {
  id: 1,
  name: "SL太郎",
  points: 1023,
});
memberListInit.set(2, {
  id: 2,
  name: "SL花子",
  points: 2435,
});
memberListInit.set(3, {
  id: 3,
  name: "ノアくん",
  points: 3245,
});
memberListInit.set(4, {
  id: 4,
  name: "Vue二郎",
  points: 7765,
});

const memberList = ref(memberListInit);

const totalPoints = computed((): number => {
  let total = 0;
  for (const member of memberList.value.values()) {
    total += member.points;
  }
  return total;
});

const onIncrementPoint = (id: number): void => {
  const member = memberList.value.get(id);
  if (member != undefined) {
    member.points++;
  }
};

const onDecrementPoint = (id: number): void => {
  const member = memberList.value.get(id);
  if (member != undefined) {
    member.points--;
  }
};

interface Member {
  id: number;
  name: string;
  points: number;
}

const hyphenCode = computed((): string => {
  return postCode.value.slice(0, 3) + "-" + postCode.value.slice(3, 7);
});

const displayDate = (): any => {
  return new Date();
};
</script>
