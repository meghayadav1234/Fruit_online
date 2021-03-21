<template>
  <v-form>
    <v-text-field label="Name" required></v-text-field>

    <v-text-field label="E-mail" required></v-text-field>

    <v-select label="Item" required></v-select>

    <v-checkbox label="Do you agree?" required></v-checkbox>

    <v-btn>Validate</v-btn>

    <v-btn color="error" class="mr-4" @click="reset">Reset Form</v-btn>

    <v-btn color="warning" @click="resetValidation">Reset Validation</v-btn>
  </v-form>
</template>
<script>
export default {
  name: "FormDetails",
  data() {
    return {
      valid: true,
      name: "",
      nameRules: [
        v => !!v || "Name is required",
        v => (v && v.length <= 10) || "Name must be less than 10 characters"
      ],
      email: "",
      emailRules: [
        v => !!v || "E-mail is required",
        v => /.+@.+\..+/.test(v) || "E-mail must be valid"
      ],
      select1: null,
      items: ["Item 1", "Item 2", "Item 3", "Item 4"],
      checkbox1: false
    };
  },

  methods: {
    validate() {
      this.$refs.form.validate();
    },
    reset() {
      this.$refs.form.reset();
    },
    resetValidation() {
      this.$refs.form.resetValidation();
    }
  }
};
</script>

<style>
</style>