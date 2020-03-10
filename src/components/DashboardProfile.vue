<template>
  <div class="dash-profile">
    <form>
      <v-text-field
        class="mt-0"
        v-model="name"
        :error-messages="nameErrors"
        label="Name"
        required
        @input="$v.name.$touch()"
        @blur="$v.name.$touch()"
      ></v-text-field>
      <div class="d-flex">
        <v-text-field
          v-model="email"
          :error-messages="emailErrors"
          label="E-mail"
          required
          @input="$v.email.$touch()"
          @blur="$v.email.$touch()"
        ></v-text-field>
        <v-icon class="ml-3" @click="add(k)">mdi-email-plus-outline</v-icon>
        <v-icon class="ml-3" @click="remove(k)">mdi-email-minus-outline</v-icon>
      </div>
      <div class="d-flex">
        <v-text-field
          v-model="phone"
          type="tel"
          :error-messages="phoneErrors"
          label="Phone Number"
          required
          @input="$v.phone.$touch()"
          @blur="$v.phone.$touch()"
        ></v-text-field>
        <v-icon class="ml-3">mdi-phone-plus</v-icon>
        <v-icon class="ml-3">mdi-phone-minus</v-icon>
      </div>
      <v-select v-model="select" :items="items" label="Gender"></v-select>
      <v-textarea
        name="address"
        label="Address"
        value
        v-model="address"
        required
        :error-messages="addressErrors"
        @blur="$v.address.$touch()"
      ></v-textarea>
      <v-file-input label="Upload Your Photo" prepend-icon="mdi-camera"></v-file-input>
      <v-textarea
        name="introduction"
        label="Self Introduction"
        value
        v-model="intro"
        required
        :error-messages="introErrors"
        @blur="$v.intro.$touch()"
      ></v-textarea>
      <v-btn class="mr-4" @click="submit">submit</v-btn>
      <v-btn @click="clear">clear</v-btn>
    </form>
  </div>
</template>

<script>
import { validationMixin } from "vuelidate";
import { required, email, minLength, numeric } from "vuelidate/lib/validators";
// import { mdiEmailPlusOutline } from '@mdi/js';

export default {
  mixins: [validationMixin],

  validations: {
    name: { required },
    email: { required, email },
    phone: { required, numeric, minLength: minLength(10) },
    address: { required },
    intro: { required }
  },

  data: () => ({
    name: "",
    email: "",
    phone: "",
    select: null,
    items: ["Male", "Female", "Other"],
    address: "",
    intro: ""
  }),

  computed: {
    nameErrors() {
      const errors = [];
      if (!this.$v.name.$dirty) return errors;
      !this.$v.name.required && errors.push("Name is required.");
      return errors;
    },
    emailErrors() {
      const errors = [];
      if (!this.$v.email.$dirty) return errors;
      !this.$v.email.email && errors.push("Must be valid e-mail");
      !this.$v.email.required && errors.push("E-mail is required");
      return errors;
    },
    phoneErrors() {
      const errors = [];
      if (!this.$v.phone.$dirty) return errors;
      !this.$v.phone.minLength &&
        errors.push("Phone number must be at least 10 digits long");
      !this.$v.phone.required && errors.push("Phone number is required");
      !this.$v.phone.numeric && errors.push("Must be a valid phone number");
      return errors;
    },
    addressErrors() {
      const errors = [];
      if (!this.$v.address.$dirty) return errors;
      !this.$v.address.required && errors.push("Address is required");
      return errors;
    },
    introErrors() {
      const errors = [];
      if (!this.$v.intro.$dirty) return errors;
      !this.$v.intro.required && errors.push("About yourself is required");
      return errors;
    }
  },

  methods: {
    submit() {
      this.$v.$touch();
    },
    clear() {
      this.$v.$reset();
      this.name = "";
      this.email = "";
      this.select = null;
      this.checkbox = false;
    }
  }
};
</script>