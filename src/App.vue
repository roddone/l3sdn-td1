<script setup>
import { ref, onMounted } from 'vue';
import AddTweet from './components/AddTweet.vue';
import TweetList from './components/TweetList.vue';
import SearchPosts from './components/SearchPosts.vue';

const post = ref({ content: 'toto', date: '', userId: '' });
const search = ref('');
const posts = ref([]);

const addPost = (content) => {
    const newPost = { ...post.value, content, date: new Date().toISOString(), userId: '123' };
    posts.value.push(newPost);
    savePostsToLocalStorage();
};

const savePostsToLocalStorage = () => {
    localStorage.setItem('posts', JSON.stringify(posts.value));
};

const getPostsFromLocalStorage = () => {
    const storedPosts = localStorage.getItem('posts');
    if (storedPosts) {
        posts.value = JSON.parse(storedPosts);
    }
};

onMounted(() => {
    getPostsFromLocalStorage();
});
</script>

<template>
    <div style="margin: 2rem;">
        <SearchPosts v-model="search" />
        <AddTweet @add-post="addPost" />
        <TweetList :posts="posts" :search="search" />
    </div>
</template>
