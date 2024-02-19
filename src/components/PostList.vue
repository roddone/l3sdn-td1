<template>
  <div>
    <ul>
      <li v-for="(post, index) in posts" :key="index" class="post-item">
        <div class="author">{{ post.author }}</div>
        <div class="date">{{ post.date }}</div>
        <div class="content">{{ post.content }}</div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    posts: Array,
  },
};
</script>

<style scoped>
.post-item {
  background-color: #f5f8fa;
  border: 1px solid #e1e8ed;
  padding: 10px;
  margin-bottom: 10px;
  border-radius: 8px;
}

.author {
  font-weight: bold;
  color: #1da1f2;
}

.date {
  color: #8899a6;
  font-size: 12px;
}

.content {
  color: #14171a;
  margin-top: 5px;
}
</style>
