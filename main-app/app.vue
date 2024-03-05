<template>
  <div>
    <Form nonvalidate @submit.prevent="onSubmit">
      Email validated input <br/>
      <Field type="email" name="email" :rules="validateEmail" />

      <div style="margin:20px; color: black">
        Error in context of main app
        <ErrorMessage name="email" />
      </div>

      <div style="margin:20px; color: red">
        Error in main app component
        <MainAppError name="email" />
      </div>

      <div style="margin:20px; color: orange">
        Error in nuxt layer component
        <LayerError name="email" />
      </div>

      <button>submit</button>
    </Form>
  </div>
</template>

<script lang="ts" setup>
import { Form, Field, ErrorMessage  } from 'vee-validate';


const localError = computed(() => {
  return useFieldError('email');
});

function onSubmit(values) {
  console.log('submit', values);
}

function validateEmail(value) {
  // if the field is empty
  if (!value) {
        return 'This field is required';
      }
      // if the field is not a valid email
      const regex = /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i;
      if (!regex.test(value)) {
        return 'This field must be a valid email';
      }
      // All is good
      return true;
}

</script>
