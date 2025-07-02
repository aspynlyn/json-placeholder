<script setup>
import Post from '@/components/Post.vue';
import { reactive, onMounted } from 'vue';

const state = reactive({
  post: {
    id: 0,
    title: '',
    body: '',
    userId: '',
  },
});

onMounted(() => {
  const passJson = history.state.data;
  if (passJson) {
    state.post = JSON.parse(passJson);
  }
});
</script>

<template>
  <h1>Detail.vue</h1>
  <post :item="state.post"></post>
</template>

<style scoped></style>
