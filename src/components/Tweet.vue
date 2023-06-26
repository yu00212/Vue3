<script setup lang="ts">
import { ref } from 'vue';
import TweetPostForm from "./TweetPostForm.vue";
import TweetList from "./TweetList.vue";

const tweets = ref([
    { id: 0, description: 'Hello, world!' },
    { id: 1, description: '2個目のツイートです'}
]);

const postTweet = (description: string) => {
  const tweet = { id: Math.random(), description:description }
  tweets.value.push(tweet)
}

const deleteTweet = (id: number) => {
  tweets.value = tweets.value.filter(t => t.id !== id)
}


</script>

<template>
  <div class="container">
    <h1>Tweeter</h1>
      <TweetPostForm @post-tweet="postTweet" />
    <div class="tweet-container">
      <p v-if="tweets.length <= 0">ツイートがありません。</p>
      <ul v-else>
        <TweetList :tweets="tweets" :delete-tweet="deleteTweet"/>
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

.form-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: aliceblue;
  padding: 24px 0;
  width: 60%;
  margin-bottom: 12px;
  border-radius: 4px;
}

input {
  margin-bottom: 16px;
}

label {
  font-size: 20px;
  font-weight: bold;
}
</style>