<script setup lang="ts">
import { ref } from 'vue';
import TweetList from './TweetList.vue';
import TweetPostForm from './TweetPostForm.vue';

const tweets = ref([{ id: 0, description: 'はじめてのつぶやきです。'}, { id: 1, description: 'ゆるくつぶやきましょう。' }])
const inputtingDescription = ref<string>('')

const postTweet = (description: string) => {
  const tweet = { id: Math.random(), description }
  tweets.value.push(tweet)
}

const deleteTweet = (id: number) => {
  tweets.value = tweets.value.filter(t => t.id !== id)
}

</script>


<template>
  <div class="container">
    <div><img class="main_icon" src="../assets/リス.svg"></div>
    <h1>ゆるつぶやき</h1>
    <p>ゆる〜く好きなことつぶやいてね</p>
    <TweetPostForm @post-tweet="postTweet" />
    <div class="tweet-container">
    <p v-if="tweets.length <= 0">No tweets have been added</p>
    <ul v-else>
      <TweetList :tweets="tweets" @delete-tweet="deleteTweet" />
    </ul>
    </div>
  </div>
</template>


<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.main_icon {
  width: 50%;
}

ul {
  padding: 0;
}
</style>