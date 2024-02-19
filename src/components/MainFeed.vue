<template>
    <label> 
        My contributions only: <input type="checkbox" @click="changeFeed()">
    </label>
    <Whatsupbar />
    <Flit flutters="getFlutters()"/>

</template>

<script setup>
import { ref, computed } from 'vue';

import Whatsupbar from './Whatsupbar.vue';
import Flit from './Flit.vue';

let overall = true;


const changeFeed = () => {
    console.log("eolmana sigani jinaya i deuli pogcheongi dwilkka?")
    overall = !overall
}

const flutters = ref([
    { user: 'woooooo', pub_time: '10:30', text: 'hello.' },
    { user: 'non.', pub_time: '10:20', text: 'Hello guys.' },
    { user: 'Raaaaaawr', pub_time: '10:10', text: '여러분들!!!! 호랑해!!!' },
    { user: 'angel', pub_time: '10:00', text: 'hiiiiii :)' },
    { user: 'LD', pub_time: '10:00', text: 'hellooo everyone! how are you ?' },
])

const getFlutters = () => {
    console.log("spring day")
    if (overall) {
        console.log("dabdabhaedo jom kidalyeojwo")
        return flutters
    } else {
        return flutters.value.filter(flutter => flutter.user == 'angel')
    }
}

</script>