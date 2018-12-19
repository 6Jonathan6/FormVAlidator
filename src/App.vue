<template>
  <div id="app">
    <email-form @badInput="onBadInput" v-model="email"/>
  </div>
</template>

<script>
import EmailForm from "@/components/EmailForm.vue";

export default {
  name: "app",
  data() {
    return {
      email: null
    };
  },
  methods: {
    onBadInput(message) {
      console.log(message);
    }
  },
  components: {
    EmailForm
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
