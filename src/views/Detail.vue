<script setup>
import httpService from '@/services/HttpService';
import Post from '@/components/Post.vue';
import { reactive, onMounted } from 'vue';
import Comment from '@/components/comment.vue';
import InputComment from '@/components/InputComment.vue';

const state = reactive({
  post: {
    id: 0,
    title: '',
    body: '',
    userId: '',
  },
  comments: [],
});

onMounted(async () => {
  const passJson = history.state.data;
  if (passJson) {
    state.post = JSON.parse(passJson);

    const commentData = await httpService.postCommentFindAll(state.post.id);
    state.comments = commentData;
  }
});

const addComment = async (comment) => {
  console.log('comment:', comment);
  const jsonBody = {
    postId: state.post.id,
    comment,
    userId: 1,
  };
  // const data = await httpService.commentSave(jsonBody);
  const data = {
    postId: 1,
    id: 4,
    name: 'alias odio sit',
    email: 'Lew@alysha.tv',
    body: comment,
  };
  state.comments.push(data);
};
</script>

<template>
  <h1>Detail.vue</h1>
  <post :item="state.post"></post>
  <hr />
  <h3>댓글들</h3>
  <input-comment @click-save="addComment"></input-comment>
  <comment v-for="item in state.comments" :item="item" :id="item.id"></comment>
</template>

<style scoped></style>
