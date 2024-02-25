<script setup>
import { ref, computed } from 'vue'
import SearchBar from './_searchbar.vue'
import AddTweet from './_addTweet.vue'
import TweetList from './_tweetList.vue'

const search = ref('')

const tweets = ref([
    { user: 'Romain', content: 'Mon premier tweet', date: new Date(2024, 1, 25, 10, 27, 0) },
    { user: 'David', content: 'Hey folks !', date: new Date(2024, 1, 25, 9, 27, 0) },
    { user: 'James', content: 'Love c#', date: new Date(2024, 0, 25, 11, 27, 0) },
])

const addNewTweet = (tweetContent) => {
    tweets.value.push({
        user: 'Romain',
        content: tweetContent,
        date: new Date()
    })
}

const filteredTweets = computed(() => {
    if(search.value)
        return tweets.value.filter(f => f.user.toLowerCase().includes(search.value.toLowerCase()))
    return tweets.value
})

</script>

<template>
    <search-bar v-model="search" />
    <add-tweet @post-tweet="addNewTweet" />
    <tweet-list :tweets="filteredTweets" >
        <template v-slot:header>
            Liste des tweets
        </template>
        <template v-slot:footer>
            Merci Elon musk !
        </template>
    </tweet-list>
</template>

<style scoped></style>
