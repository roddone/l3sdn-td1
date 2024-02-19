<template>
  <div class="app">
    <!-- Barre de navigation -->
    <div class="sidebar">
      <ul>
        <boutton class="">Accueil</boutton>
        <li><i class="fas fa-home"></i> Accueil</li>
        <li><i class="fas fa-compass"></i> Explorer</li>
        <li><i class="fas fa-bell"></i> Notifications</li>
        <li><i class="fas fa-envelope"></i> Messages</li>
        <li><i class="fas fa-bookmark"></i> Signets</li>
        <li><i class="fas fa-list"></i> Listes</li>
        <li><i class="fas fa-user"></i> Profil</li>
        <li><i class="fas fa-plus"></i> Plus</li>
      </ul>
    </div>

    <!-- Actualités -->
    <div class="main-content">
      <iframe src="https://twitter.com" width="100%" height="600px"></iframe>
    </div>

    <!-- Case de recherche Twitter -->
    <div class="search">
      <input type="text" placeholder="Rechercher sur Twitter">
      <button>Rechercher</button>
    </div>
  </div>
</template>

<script>
import '@fortawesome/fontawesome-free/css/all.css';

export default {
  name: 'App',
  data() {
    return {
      // Données du composant
    }
  },
  methods: {
    // Méthodes du composant
  }
}
</script>

<style>
.app {
  display: flex;
}

.sidebar {
  width: 200px;
  background-color: #f0f0f0;
  padding: 20px;
}

.sidebar ul {
  list-style: none;
  padding: 0;
}

.sidebar ul li {
  margin-bottom: 10px;
}

.sidebar ul li i {
  margin-right: 10px;
}

.main-content {
  flex-grow: 1;
  padding: 20px;
}

.search {
  width: 200px;
  padding: 20px;
}
</style>
