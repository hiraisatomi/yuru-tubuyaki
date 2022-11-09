<script setup lang="ts">
import { defineProps } from 'vue';
import TweetPostFormVue from './TweetPostForm.vue';

type Tweet = {
  id: number,
  description: string,
}

type Props = {
  tweets: Tweet[]
}

defineProps<Props>()
const emit = defineEmits(['delete-tweet'])
const deleteTweet = (id: number) => {
  emit('delete-tweet', id)
}

</script>

<template>
  <li v-for="tweet in tweets" :key="tweet.id" class="tweet-list">
    <span>{{ tweet.description }}</span>
    <button class="delete-button" @click="deleteTweet(tweet.id)">delete</button>
  </li>
</template>


<style scoped>
.delete-button {
  background-color: rgb(248, 147, 129);
}

.tweet-list {
  list-style: none;
  margin-bottom: 12px;
  border-radius: 4px;
  align-items: center;
  font-size: 12px;
  display: flex;
  justify-content: space-between;
  background-color: rgb(204, 219, 233);
  padding: 8px 20px;
}
</style>