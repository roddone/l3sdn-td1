<template>
    <div class="sidebar">
      <div class="sidebar-header">
        <img src="./assets/twitter_logo.png" alt="Twitter Logo" class="logo">
      </div>
      <div class="sidebar-content">
        <div class="search-bar">
          <input type="text" placeholder="Search Twitter">
          <button><i class="fa fa-search"></i></button>
        </div>
        <h3 class="section-title">Trends for You</h3>
        <ul class="trend-list">
          <li v-for="trend in trends" :key="trend.id">{{ trend.name }}</li>
        </ul>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        trends: [
          { id: 1, name: 'Trend 1' },
          { id: 2, name: 'Trend 2' },
          { id: 3, name: 'Trend 3' },
          
        ]
      };
    }
  };
  </script>
  
  <style scoped>
  .sidebar {
    width: 280px;
    background-color: #15202b;
    color: #fff;
    height: 100vh;
    overflow-y: auto;
  }
  
  .sidebar-header {
    padding: 20px;
  }
  
  .sidebar-content {
    padding: 20px;
  }
  
  .logo {
    width: 100px;
    height: auto;
  }
  
  .section-title {
    font-size: 18px;
    margin-bottom: 15px;
  }
  
  .trend-list {
    list-style: none;
    padding: 0;
  }
  
  .trend-item {
    cursor: pointer;
    margin-bottom: 8px;
  }
  
  .trend-item:hover {
    color: #1da1f2;
  }
  
  .search-bar {
    margin-bottom: 20px;
  }
  
  .search-bar input[type="text"] {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    margin-bottom: 10px;
  }
  
  .search-bar button {
    background-color: #1da1f2;
    color: #fff;
    border: none;
    border-radius: 5px;
    padding: 10px;
    cursor: pointer;
  }
  
  .search-bar button:hover {
    background-color: #0c7cb0;
  }
  
  .fa-search {
    font-size: 18px;
  }
  </style>
  