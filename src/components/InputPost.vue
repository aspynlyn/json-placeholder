<script setup>
import { reactive } from 'vue';

const emit = defineEmits(['click-post']);

const state = reactive({
  title: '',
  body: '',
});

const submit = () => {
  emit('click-post', state);
  state.title = '';
  state.body = '';
};
</script>

<template>
  <div class="mb-3">
    <label for="title" class="form-label">제목</label>
    <input
      type="text"
      class="form-control"
      id="title"
      placeholder="3~20자"
      v-model="state.title"
    />
  </div>
  <div class="mb-3">
    <label for="body" class="form-label">내용</label>
    <textarea
      id="body"
      placeholder="3~200자"
      v-model="state.body"
    ></textarea>
  </div>
  <div class="mb-3">
    <button type="button" class="btn btn-success" @click="submit">저장</button>
  </div>
</template>

<style scoped></style>
