<template>
  <div>
    <ul>
      <li v-for="(post, index) in randomPosts" :key="index">
        {{ post.content }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    randomPosts: Array,
  },
};
</script>
