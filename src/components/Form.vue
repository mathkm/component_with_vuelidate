<template>
  <div>
    <v-text-field
      label="Name"
      v-model="form.name"
      :error-messages="nameError"
      @input="update('name',$event)"
      @blur="update('name',$event.target.value)"
      required
    />
    <v-text-field
      label="E-mail"
      v-model="form.email"
      @input="update('email',$event)"
      @blur="update('email',$event.target.value)"
      :error-messages="emailError"
    />
  </div>
</template>

<script>
export default {
  name: "Form",
  props: {
    form: Object,
    validates: Object
  },
  methods: {
    update(key, value) {
      this.form[key] = value;
      this.$emit("input", this.form);
      this.validates[key].$touch();
    }
  },
  computed: {
    nameError() {
      let errors = [];
      if (!this.validates.name.$dirty) return errors;
      !this.validates.name.required && errors.push("Name is Required.");
      return errors;
    },
    emailError() {
      let errors = [];
      if (!this.validates.email.$dirty) return errors;
      !this.validates.email.email && errors.push("Please input E-MAIL.");
      return errors;
    }
  }
};
</script>