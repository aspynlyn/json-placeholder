<script setup>
import { useRouter } from 'vue-router';

const router = useRouter();

const props = defineProps({
  item: Object,
});

const json = JSON.stringify(props.item);

const moveToDetail = () => {
  router.push({
    path: '/detail',
    state: {
      data: json,
    },
  });
};
// 라우팅 처리 /detail로 이동
// props.item을 JSON 문자열로 변경하여 state.data에 대입
</script>

<template>
  <div class="card mb-3 pointer" @click="moveToDetail">
    <div class="card-body">
      <h3 class="card-title">{{ props.item.title }}</h3>
      <div class="card-subtitle text-muted">{{ props.item.body }}</div>
    </div>
  </div>
</template>

<style scoped></style>
