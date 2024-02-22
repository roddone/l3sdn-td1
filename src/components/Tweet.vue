<template>
    <div>
      <p>{{ author }} - {{ timeAgo }}</p>
      <p>{{ tweetContent }}</p>
      <p><button>Répondre</button><button>Retweeter</button><button>Aimer</button></p>
    </div>
  </template>
  
  <script>
  export default {
    props: ['tweetContent', 'timeAgo', "author"]
  };
  </script>
  