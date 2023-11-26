<template>
    <section class="section-style">
      <div class="flex-container">
        <div class="text-hero">
          <img src="" alt="" srcset="">
          <h1>Let's help you get started with our bussines</h1>
          <p>Our registration is a simple and quick process that takes no longer than 7 minutes to complete.</p>
          <div class="card-hero">
            <!-- <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Aperiam earum quos assumenda tempore iusto
              voluptates a cupiditate unde accusamus voluptatibus nihil veniam ad iste laboriosam deleniti, atque voluptatem
              nisi blanditiis?</p> -->
          </div>
        </div>
        <card class="card-section" style="width: 450px; ">
          <h1>Get Started</h1>
          <p>Create your account now</p>
          <form @submit.prevent="sendEmail">
            <div class="form-group">
              <KInput class="form-input" :style="{ width: '290px' }" name="Name" placeholder="Name"></KInput>
            </div>
            <div class="form-group">
              <KInput class="form-input" :style="{ width: '290px' }" name="eamil" placeholder="Email" v-model="email">
              </KInput>
            </div>
            <div class="form-group">
              <KInput class="form-input" :style="{ width: '290px' }" name="password" placeholder="password"
                v-model="password"></KInput>
            </div>
            <div class="example-col">
              <kButton :style="{ width: '100px' }" id="submit-btn">Sign Up</kButton>
            </div>
            <div class="example-col">
              <p>Have an account ? Login</p>
            </div>
          </form>
        </card>
      </div>
    </section>
  </template> 

<script>
import { Client, Account } from "appwrite";
const client = new Client();
client.setEndpoint("add localhost id ").setProject("input project id here");
const account = new Account(client);
export { client, account };
import {
  Card,
} from "@progress/kendo-vue-layout";
// ES2015 module syntax
import { Input } from "@progress/kendo-vue-inputs";
import "@progress/kendo-theme-default";
import { Button } from "@progress/kendo-vue-buttons";
export default {
  name: "CardComponent",
  components: {
    card: Card,
    KInput: Input,
    kButton: Button,
  },
  data() {
    return {
      name: '',
      email: '',
      password: '',
      error: ''
    }
  },
  methods: {
    async sendEmail() {
      try {
        const user = await account.create("unique()", this.email, this.password, this.name)
        console.log(user); // Success
      } catch (error) {
        console.log(error); // Failure
      }
    }
  },
};
</script>