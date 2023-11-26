<script setup>
import { user } from "../lib/stores/user.js";
import { ref } from "vue";

const email = ref("");
const password = ref("");
</script>

<template>
  <section>
    <h1>Login or register</h1>
    <form>
      <input type="email" placeholder="Email" v-model="email" />
      <input type="password" placeholder="Password" v-model="password" />
      <div>
        <button type="button" @click="user.login(email, password)">
          Login
        </button>
        <button type="button" @click="user.register(email, password)">
          Register
        </button>
      </div>
    </form>
  </section>
</template>
