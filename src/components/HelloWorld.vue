<template>
  <v-form>
    <Form :form="form" :validates="$v.form" />
    <div>
      <div>Parent can get inputed values and validate result</div>
      <div>values</div>
      <div>{{ form }}</div>
      <div>Validations</div>
      <div>{{ $v.form.name }}</div>
      <div>{{ $v.form.email }}</div>
    </div>
    <div>
      <v-btn :disabled="!$v.form.$anyDirty || $v.form.$anyError">Submit</v-btn>
    </div>
  </v-form>
</template>
<script>
import Form from "../components/Form";
import { required, email } from "vuelidate/lib/validators";

export default {
  name: "HelloWorld",
  components: {
    Form
  },
  data: () => ({
    form: {
      name: "",
      email: ""
    }
  }),
  validations: {
    form: {
      name: { required },
      email: { email }
    }
  }
};
</script>
