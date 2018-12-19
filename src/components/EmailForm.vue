<template>
  <form-validator :watchHandler="inputHandler" message="El email es obligatorio y debe contener @">
    <div slot-scope="{inputProps, inputEvents}">
      <label for="email">Email</label>
      <input v-bind="inputProps" v-on="inputEvents" id="email" type="email">
    </div>
  </form-validator>
</template>
<script>
import FormValidator from "./FormValidator.vue";
export default {
  name: "EmailForm",
  methods: {
    inputHandler(newInput) {
      let email = newInput.trim();
      email = email.replace(/\s/g, "");
      const regex = /.*@.*/g;
      console.log(email);
      const isValid = !email.match(regex)
        ? false
        : email.match(regex)[0] === email;
      return { isValid, value: email };
    }
  },
  components: {
    FormValidator
  }
};
</script>
