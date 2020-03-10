<template>
  <div class="Login h-100">
    <v-container class="align-center container d-flex h-100 justify-center">
      <v-card class="mx-auto pa-10" width="450" max-width="100%">
        <h1>Login</h1>
        <form>
          <v-text-field
            v-model="email"
            :error-messages="emailErrors"
            label="E-mail"
            required
            @input="$v.email.$touch()"
            @blur="$v.email.$touch()"
          ></v-text-field>
          <v-text-field
            v-model="password"
            :error-messages="passwordErrors"
            :counter="6"
            label="Password"
            required
            @input="$v.password.$touch()"
            @blur="$v.password.$touch()"
          ></v-text-field>
          <!-- <v-checkbox
            v-model="checkbox"
            :error-messages="checkboxErrors"
            label="Do you agree?"
            required
            @change="$v.checkbox.$touch()"
            @blur="$v.checkbox.$touch()"
          ></v-checkbox> -->

          <v-card-actions>
            <v-btn class="mr-4 primary" @click="submit">submit</v-btn>
            <v-btn @click="clear">clear</v-btn>
          </v-card-actions>
        </form>
      </v-card>
    </v-container>
  </div>
</template>

<script>
import axios from 'axios';
import { validationMixin } from "vuelidate";
import { required, email } from "vuelidate/lib/validators";

export default {
  name: "login",
  mixins: [validationMixin],

  validations: {
    email: { required, email },
    password: { required }
  },

  data: () => ({
    email: "",
    password: ""
  }),

  computed: {
    passwordErrors() {
      const errors = [];
      if (!this.$v.password.$dirty) return errors;
      !this.$v.password.required && errors.push("Password is required.");
      return errors;
    },
    emailErrors() {
      const errors = [];
      if (!this.$v.email.$dirty) return errors;
      !this.$v.email.email && errors.push("Must be valid e-mail");
      !this.$v.email.required && errors.push("E-mail is required");
      return errors;
    }
  },

  methods: {
    submit() {
      this.$v.$touch();
      this.$router.push({ path: '/dashboard'})
      // const logData = {
      //     email: this.email,
      //     password: this.password
      // }
      // console.log(logData)
      axios.get('https://portfolio-5c3fe.firebaseio.com/users.json')
      .then(res => {
        console.log(res.data);
        const data = res.data;
        const users = [];
        for( let key in data){
          const user = data[key];
          user.id = key;
          users.push(user);
        }
        for(let i in users){
          console.log(users[i].email);

          if((users[i].email == this.email) && (users[i].password == this.password)){
            console.log('sss');
            // this.$router.push({ path: '/dashboard'})
          }else{
            console.log('nnn');
          }
        }
      })
      .catch(err =>{console.log(err)});
    },
    clear() {
      this.$v.$reset();
      this.name = "";
      this.password =""
    }
  },
  mounted(){
    
  }
};
</script> 

<style scoped>
.h-100 {
  height: 100%;
}
</style>