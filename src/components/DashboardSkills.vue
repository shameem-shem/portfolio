<template>
  <div class="dash-skills">
    <form>
      <v-row v-for="(skill, i) in skillset" :key="i">
        <v-col>
          <v-text-field
            class="mt-0"
            v-model="skillset[i].technology"
            label="Technology"
            :error-messages="technologyErrors"
            required
            @input="$v.technology.$touch()"
            @blur="$v.technology.$touch()"
          ></v-text-field>
        </v-col>
        <v-col>
          <v-text-field
            class="mt-0"
            v-model.number="skillset[i].knowledge"
            :error-messages="knowledgeErrors"
            label="Knowledge"
            required
            @input="$v.knowledge.$touch()"
            @blur="$v.knowledge.$touch()"
          ></v-text-field>
        </v-col>
        <v-col>
          <v-icon @click="addRow()">mdi-email-plus-outline</v-icon>
          <v-icon @click="removeRow(indx)">mdi-email-minus-outline</v-icon>
        </v-col>
      </v-row>
      <v-btn class="mr-4">Save</v-btn>
    </form>
  </div>
</template>

<script>
import { validationMixin } from "vuelidate";
import { required } from "vuelidate/lib/validators";

export default {
  mixins: [validationMixin],
  validations: {
    technology: { required },
    knowledge: { required }
  },
  data: () => ({
    skillset: [
      { technology: "", knowledge: "" }
    ]
  }),
  computed: {
    technologyErrors() {
      const errors = [];
      if (!this.$v.technology.$dirty) return errors;
      !this.$v.technology.required && errors.push("Required.");
      return errors;
    },
    knowledgeErrors() {
      const errors = [];
      if (!this.$v.knowledge.$dirty) return errors;
      !this.$v.knowledge.required && errors.push("Required.");
      return errors;
    }
  },
  methods: {
    addRow() {
      this.skillset.push(
        { technology: "", knowledge: "" }
      )
    },
    removeRow(indx) {
      this.skillset.splice(indx,1)
    },
   
    // submit(){
    //   this.$v.$touch();
    // }
  }
};
</script>