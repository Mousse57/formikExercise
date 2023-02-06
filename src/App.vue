<template>
  <Formik class="formik"
    :initialValues="{ name: '', email: '', password: ''}"
    :onSubmit="handleSubmit"
    :validate="validate"
  />
</template>
<script>
import { ref } from 'vue';
import Formik from './components/Formik.vue';

export default {
  name: 'App',
  components: {
    Formik,
  },
  data() {
    return {
      submitting: false,
    };
  },
  methods: {
    toggleSubmitting() {
      this.submitting = !this.submitting;
    },
    handleSubmit(values) {
      this.toggleSubmitting();
      const errors = this.validateForm(values);
      if (Object.keys(errors).length === 0) {
        alert('Form is valid');
      } else {
        let errorMessage = '';
        for (const [key, value] of Object.entries(errors)) {
          errorMessage += `${key}: ${value} \n`;
        }
        alert(errorMessage);
      }
      this.toggleSubmitting();
    },
    validateForm(values) {
      let formErrors = {};
      if (!values.email) {
        formErrors.email = 'Required';
      } else if (!/^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}$/i.test(values.email)) {
        formErrors.email = 'Invalid email address';
      }
      if (!values.password) {
        formErrors.password = 'Required';
      } else if (values.password.length < 8) {
        formErrors.password = 'Password must be at least 8 characters';
      }
      if (!values.name) {
        formErrors.name = 'Required';
      } else if (values.name.length < 3) {
        formErrors.name = 'Name must be at least 3 characters';
      }
      return formErrors;
    },
  },
};
</script>