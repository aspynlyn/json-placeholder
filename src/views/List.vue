<script setup>
import { reactive, onMounted } from 'vue';
import httpService from '@/services/HttpService';
import Post from '@/components/Post.vue';
import InputPost from '@/components/InputPost.vue';

const state = reactive({
  postList: [],
});
onMounted(() => {
  findAll();
});

const findAll = async () => {
  const data = await httpService.postFindAll();
  console.log('data:', data);

  state.postList = data;
};

const submit = async (post) => {
  console.log('post', post);
  const jsonBody = {
    title: post.title,
    body: post.body,
    userId: 2,
  };
  const data = await httpService.postSave(jsonBody);
  // const data = {
  //   id: 101,
  //   title: post.title,
  //   body: post.body,
  //   userId: 2,
  // };
  state.postList.unshift(data);
};
</script>

<template>
  <h1>List.vue</h1>
  <input-post @click-post="submit"></input-post>
  <post v-for="item in state.postList" :key="item.id" :item="item"></post>
</template>

<style scoped></style>
