<template>
    <div>
      <p v-if="loading">Loading...</p>
      <p v-else>Hello, {{ userName }}!</p>
    </div>
  </template>
  
  <script>
  import { Appwrite } from 'appwrite';
  
  export default {
    data() {
      return {
        userName: '',
        loading: true,
      };
    },
    async created() {
      const sdk = new Appwrite();
  
      sdk
        .setEndpoint('YOUR_APPWRITE_ENDPOINT') // Replace with your Appwrite endpoint
        .setProject('YOUR_PROJECT_ID'); // Replace with your project ID
  
      try {
        const response = await sdk.account.get();
        this.userName = response.name;
      } catch (error) {
        console.error('Error fetching user name:', error);
      } finally {
        this.loading = false;
      }
    },
  };
  </script>