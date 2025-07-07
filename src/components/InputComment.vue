<script setup>
import { reactive } from 'vue';

const emit = defineEmits(['click-save']);

const state = reactive({
  comment: '',
});

const addComment = () => {
  emit('click-save', state.comment);
  state.comment = '';
};
</script>

<template>
  <label for="">댓글: <input type="text" v-model="state.comment" /></label>
  <button @click="addComment">저장</button>
  <!-- emit은 전달받은 함수를 호출할 때 쓰는 놈, 이벤트를 연결할 땐 props필요없음 -->
</template>

<style scoped></style>
