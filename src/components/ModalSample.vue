<template>
  <button class="modal-button" v-on:click="open">OPEN</button>
  <teleport to="#target">
    <div class="modal" v-show="isVisible">
      <div class="modal-content">
        <p>モーダルの内容</p>
        <button v-on:click="close">close</button>
      </div>
    </div>
  </teleport>
</template>
<script setup lang="ts">
interface Props {
  isVisible: boolean;
}

interface Emits {
  (event: "open"): void;
  (event: "close"): void;
}

const props = defineProps<Props>();
const emit = defineEmits<Emits>();

const open = (): void => {
  emit("open");
};

const close = (): void => {
  emit("close");
};
</script>
<style scoped>
.modal-button {
  margin: 50px;
}
.modal {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  background-color: rgba(0, 0, 0, 0.5);
}
.modal-content {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: white;
  width: 500px;
  border-radius: 10px;
  padding: 20px;
}
</style>
