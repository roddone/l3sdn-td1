<template>
    <div class="container">
        <div class="twitter-box">
            <div class="twitter-header">
                <h1>{{ title }}</h1>
            </div>
  
            <Post @add-input="(e) => add(e)" />
  
            <div class="twitter-posts">
                <div v-for="(item, index) in filteredtl" :key="index" class="post">
                    <div class="post-header">
                        <img :src="item.user.avatar" alt="Avatar">
                        <p>{{ item.user.name }}</p>
                    </div>
                    <p>{{ item.value }}</p>
                    <p class="post-time">{{ item.time }}</p>
                </div>
            </div>
        </div>
    </div>
</template>
  
<script setup>
    import { ref, computed } from "vue";
    import Post from './post.vue'
  
    const title = 'Twitter';
    const tl = ref([]);

    const filteredtl = computed(() => [...tl.value].sort((a,b)=>b.date - a.date))
  
    const add = (valeurInput) => {
        const currentTime = new Date().toLocaleString();
        tl.value.push({ user: users[Math.floor(Math.random() * users.length)], value: valeurInput.value, time: currentTime });
        valeurInput.value = '';
    };
  
    const users = [
        { name: 'John Doe', avatar: 'https://randomuser.me/api/portraits/men/1.jpg' },
        { name: 'Jane Smith', avatar: 'https://randomuser.me/api/portraits/women/2.jpg' },
        { name: 'Bob Johnson', avatar: 'https://randomuser.me/api/portraits/men/3.jpg' }
    ];

    const fauxTweets = [
        {
            user: { name: 'John Doe', avatar: 'https://randomuser.me/api/portraits/men/1.jpg' },
            value: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque euismod, urna nec laoreet consectetur, magna arcu posuere est, nec euismod mi turpis a felis.",
            time: "2024-02-19 17:28:00"
        },
        {
            user: { name: 'Jane Smith', avatar: 'https://randomuser.me/api/portraits/women/2.jpg' },
            value: "Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Proin nec mauris nec leo posuere mattis.",
            time: "2024-02-19 11:45:00"
        },
        {
            user: { name: 'Bob Johnson', avatar: 'https://randomuser.me/api/portraits/men/3.jpg' },
            value: "Duis non lacus interdum, lacinia ex nec, tempus nunc. Nulla facilisi. Phasellus sit amet justo non augue fringilla tristique a nec libero.",
            time: "2024-02-19 08:15:00"
        }        
        ];

        fauxTweets.forEach(tweet => {
            tl.value.push(tweet);
        });
</script>
  
<style scoped>
    .container {
        display: flex;
    }
  
    .twitter-box {
        width: 400px;
        border: 1px solid #ccc;
        border-radius: 10px;
        padding: 20px;
    }
  
    .twitter-header h1 {
        font-size: 24px;
        margin-bottom: 20px;
    }
  
    .twitter-posts {
        border-top: 1px solid #ccc;
        padding-top: 20px;
    }
  
    .post {
        padding: 10px;
        border-bottom: 1px solid #ccc;
    }
  
    .post-header {
        display: flex;
        align-items: center;
        margin-bottom: 5px;
    }
    
    .post-header img {
        width: 30px;
        height: 30px;
        border-radius: 50%;
        margin-right: 10px;
    }
    
    .post p {
        margin: 0;
        font-size: 16px;
    }
  
    .post-time {
        color: #666;
        font-size: 3px;
    }
</style>  