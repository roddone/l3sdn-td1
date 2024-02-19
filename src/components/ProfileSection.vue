<template>
    <div class="profile-section mb-4">
      <div class="profile-info">
        <img :src="profilePicture" alt="Profile Picture" class="profile-picture">
        <div class="profile-details">
          <h2>Your Profile</h2>
          <p>Name: Elie jbeili</p>
          <p>Username: @Eliejb</p>
          <p>Bio: Web Developer | Passionate about Vue.js</p>
        </div>
      </div>
      <input type="file" accept="image/*" @change="onFileChange">
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        profilePicture: '',
      };
    },
    methods: {
      onFileChange(event) {
        const file = event.target.files[0];
        this.profilePicture = URL.createObjectURL(file);
      }
    }
  };
  </script>
  

  