<template>
    <div>
      <p>{{ tweetContent }} - {{ timeAgo }}</p>
      <p><button>Répondre</button><button>Retweeter</button><button>Aimer</button></p>
    </div>
  </template>
  
  <script>
  export default {
    props: ['tweetContent', 'timeAgo']
  };
  </script>
  