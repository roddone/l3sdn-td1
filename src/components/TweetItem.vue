<script>
    export default {
    props: {
        tweet: {
        type: Object,
        required: true,
        },
    }
    };
</script>

<template>
    <div class="tweet-item">
      <img :src="tweet.profilePicture" alt="Profile" />
      <div class="tweet-details">
        <p><strong>@{{ tweet.username }}</strong></p>
        <p>{{ tweet.content }}</p>
        <p>Posted {{ tweet.postedAt }}</p>
      </div>
    </div>
  </template>
  
<style>
    .tweet-item {
        border-color: aqua;
        border-width: 1px;
        border-style: solid;
        border-radius: 10px;
    }

    img {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    }
</style>
  