<template>
    <div>
        <slot name="header"></slot>
    </div>
    <div>
        <ul>
            <li v-for="tweet in tweets">
                <tweet-details :tweet="tweet" />
            </li>
        </ul>
    </div>
    <div>
        <slot name="footer">un contenu par défaut ...</slot>
    </div>
</template>

<script setup>
import TweetDetails from './_tweetDetails.vue'
const props = defineProps(['tweets'])

</script>