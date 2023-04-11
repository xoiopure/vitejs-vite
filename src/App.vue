<script setup>
import { useForm } from 'vee-validate';
import * as yup from 'yup';

const schema = yup.object({
  email: yup.string().email().required(),
  name: yup.string().required(),
});

const { useFieldModel, errors, handleSubmit } = useForm({
  validationSchema: schema,
});

const [email, name] = useFieldModel(['email', 'name']);

const onSubmit = handleSubmit((values) => {
  alert(JSON.stringify(values, null, 2));
});
</script>

<template>
  <form @submit="onSubmit">
    <input v-model="email" name="email" type="email" />
    <span>{{ errors.email }}</span>

    <input v-model="name" name="name" />
    <span>{{ errors.name }}</span>

    <button>Submit</button>
  </form>
</template>
