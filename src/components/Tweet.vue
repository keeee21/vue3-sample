<script setup lang="ts">
import { ref } from 'vue';
import TweetPostForm from './TweetPostForm.vue';
import TweetList from './TweetList.vue';

type Tweet = {
  id: number;
  description: string;
}

const title = ref<string>('Tweeter');

const tweets = ref([
  {
    id: 0,
    description: 'Hello World',
  },
  {
    id: 1,
    description: 'Second Tweet',
  },
]);


const postTweet = (description: string) => {
  const tweet = {
    id: Math.random(),
    description
  }
  tweets.value.push(tweet);
}

const deleteTweet = (id: number) => {
  tweets.value = tweets.value.filter((tweet :Tweet) => tweet.id !== id);
}

</script>

<template>
  <div class="container">
    <h1>{{ title }}</h1>
    <TweetPostForm @post-tweet="postTweet"/>
    <div class="tweet-container">
      <p v-if="tweets.length <= 0">No tweets have been added</p>
      <ul>
        <TweetList :tweets="tweets" @delete-tweet="deleteTweet"/>
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

input {
  margin-bottom: 16px;
}

label {
  font-size: 20px;
  font-weight: bold;
}
</style>
