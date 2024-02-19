<template>
    <div class="flex min-h-screen bg-gray-100">
      <!-- Left Sidebar -->
      <aside class="w-1/5 bg-white">
        <div class="flex flex-col items-center">
          <!-- Twitter Logo -->
          <img src="./assets/twitter.png" alt="Twitter Logo" class="w-15 h-20 my-4">
          <div class="my-4 w-full px-4">
            <ul>
              <li class="flex items-center my-2 text-black">
                <!-- Home Icon -->
                <img src="./assets/home.png" alt="Home" class="w-5 h-5 mr-2">
                Home
              </li>
              <!-- Other menu items -->
            </ul>
          </div>
          <button class="px-6 py-2 rounded-full bg-blue-400 text-white">Tweet</button>
        </div>
      </aside>
  
      <!-- Main Content -->
      <main class="w-3/5 border-x border-gray-300">
        <div class="p-4">
          <div class="flex items-center mb-4">
            <!-- Profile Picture -->
            <img src="./assets/icon.jpg" alt="Profile" class="w-10 h-10 rounded-full mr-2">
            <input type="text" placeholder="What's happening?" class="w-full p-4 border rounded-full" />
          </div>
          <!-- Add tweet items here -->
        </div>
      </main>
  
      <!-- Right Sidebar -->
      <aside class="w-1/5 bg-white">
        <div class="p-4">
          <div class="flex items-center space-x-2 mb-4">
            <input type="text" placeholder="Search Twitter" class="p-2 border rounded-full flex-grow text-black" />
            <svg class="w-6 h-6 text-gray-600" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <!-- SVG path for search icon -->
            </svg>
          </div>
          <!-- Trends and suggestions will go here -->
        </div>
      </aside>
    </div>
  </template>
  
  <script>
  export default {
    name: 'TwitterLayout',
    data() {
      return {
        // Data properties for static content
      };
    },
  };
  </script>
  
  <style scoped>
  @import 'https://cdn.jsdelivr.net/npm/tailwindcss@2.1.2/dist/tailwind.min.css';
  </style>
  