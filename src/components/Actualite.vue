<template>
    <div class="message">
      <h2>Actualités</h2>
      <div v-if="tweets.length > 0">
        <div v-for="tweet in tweets" :key="tweet.id">
          <h3>{{ tweet.author }}</h3>
          <p>{{ formatDateTime(tweet.date) }}</p>
          <p>{{ tweet.content }}</p>
        </div>
      </div>
      <input type="text" v-model="newTweet" placeholder="Quoi de neuf ?">
      <button @click="postTweet">Tweeter</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTweet: '',
        tweets: [
          { id: 1, author: 'FootballFan', date: '2024-03-06 12:00', content: 'Le Real Madrid remporte la Ligue des Champions pour la 14ème fois ! #ChampionsLeague #RealMadrid' },
          { id: 2, author: 'SoccerExpert', date: '2024-03-06 12:30', content: 'Le FC Barcelone est en négociations pour signer une jeune star brésilienne. #Transferts #FCBarcelona' },
          { id: 3, author: 'GoalGetter', date: '2024-03-06 13:00', content: "L'équipe nationale d'Angleterre annonce son nouveau sélectionneur après la démission de Gareth Southgate. #ThreeLions" },
          { id: 4, author: 'FootballGossip', date: '2024-03-06 13:30', content: 'Le PSG serait sur le point de finaliser un accord pour recruter une superstar mondiale lors du prochain mercato estival. #PSG #Mercato' },
          { id: 5, author: 'SoccerNews', date: '2024-03-06 14:00', content: 'Le Bayern Munich annonce la prolongation de contrat de son attaquant vedette pour cinq saisons supplémentaires. #BayernMunich #Bundesliga' },
          { id: 6, author: 'FootballInsider', date: '2024-03-06 14:30', content: 'Un jeune prodige argentin attire l\'attention des grands clubs européens après ses performances exceptionnelles en Copa Libertadores. #Transferts #FutureStar' },
          { id: 7, author: 'GoalMachine', date: '2024-03-06 15:00', content: 'Le Ballon d\'Or 2024 est décerné à un joueur de l\'Atlético Madrid pour la première fois depuis des années. #BallondOr #LaLiga' },
          { id: 8, author: 'SoccerStats', date: '2024-03-06 15:30', content: "Un club de Premier League effectue un changement d'entraîneur en plein milieu de la saison après une série de mauvais résultats. #EPL #ManagerialChange" }
        ]
      };
    },
    methods: {
      postTweet() {
        if (this.newTweet.trim() !== '') {
          this.tweets.push({
            id: this.tweets.length + 1,
            author: 'Anonymous',
            date: new Date().toISOString(),
            content: this.newTweet.trim()
          });
          this.newTweet = '';
        }
      },
      formatDateTime(dateTime) {
        const options = { year: 'numeric', month: 'short', day: 'numeric', hour: '2-digit', minute: '2-digit' };
        return new Date(dateTime).toLocaleDateString('en-US', options);
      }
    }
  };
  </script>
  