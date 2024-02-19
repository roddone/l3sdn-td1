<template>
    <div>
        <TweetForm @add-tweet="addTweet" />
        <div v-for="tweet in tweets" :key="tweet.date">
            <div class="ml-4">
                <p class="font-semibold"><b>@{{ tweet.name }}:</b> {{ tweet.date }}</p>
            </div>
            <p class="text-gray-800 mt-4">{{ tweet.message }}</p>
        </div>
    </div>
    
</template>

<script setup>
    import { ref } from 'vue';
    import TweetForm from './TweetForm.vue';

    const tweets = ref([
    {
        'name': 'John Doe',
        'message': 'Lorem ipsum dolor sit amet,  luctus nunc nec, tincidunt nunce.',
        'date': new Date().getDate() + '/' + new Date().getMonth() + '/' + new Date().getFullYear() + ' ' + new Date().getHours() + ':' + new Date().getMinutes() + ':' + new Date().getSeconds(),
        }, 
        {
        'name': 'Max max',
        'message': 'consectetur adipiscing elit. Morbi nec odio tempus,',
        'date': new Date().getDate() + '/' + new Date().getMonth() + '/' + new Date().getFullYear() + ' ' + new Date().getHours() + ':' + new Date().getMinutes() + ':' + new Date().getSeconds(),
    }, {
        'name': 'Ella Bella',
        'message': 'Nam mattis laoreet ligula sit amet pellentesque. Donec gravida enim quis est aliquet, sed pellentesque odio pulvinar.',
        'date': new Date().getDate() + '/' + new Date().getMonth() + '/' + new Date().getFullYear() + ' ' + new Date().getHours() + ':' + new Date().getMinutes() + ':' + new Date().getSeconds(),
        }, 
        {
        'name': 'Monkeyy',
        'message': 'Sed euismod quis urna vel commodo. Aenean hendrerit nisl sed viverra sodales.',
        'date': new Date().getDate() + '/' + new Date().getMonth() + '/' + new Date().getFullYear() + ' ' + new Date().getHours() + ':' + new Date().getMinutes() + ':' + new Date().getSeconds(),
    }, 
    {
        'name': 'Sonniic',
        'message': 'Aliquam rhoncus hendrerit hendrerit. Maecenas risus erat',
        'date': new Date().getDate() + '/' + new Date().getMonth() + '/' + new Date().getFullYear() + ' ' + new Date().getHours() + ':' + new Date().getMinutes() + ':' + new Date().getSeconds(),
        }, 
        {
        'name': 'Peachh',
        'message': 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi nec odio tempus, luctus nunc nec, tincidunt nunce.',
        'date': new Date().getDate() + '/' + new Date().getMonth() + '/' + new Date().getFullYear() + ' ' + new Date().getHours() + ':' + new Date().getMinutes() + ':' + new Date().getSeconds(),
    }
    ]);

    const addTweet = (newTweet) => {
        tweets.value.push(newTweet); // Ajoute le nouveau tweet à la liste
        
    };
</script>
