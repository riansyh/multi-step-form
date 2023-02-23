<template>
  <div class="flex flex-col gap-6 fade-in">
    <div class="form-group flex flex-col gap-2">
      <div class="label flex justify-between">
        <label for="name">Name</label>
        <p v-if="formError.name" class="error-text">This field is required</p>
      </div>
      <Field
        name="name"
        type="text"
        placeholder="e.g. Stephen King"
        class="input-field"
        v-model="formValue.name"
      ></Field>
    </div>
    <div class="form-group flex flex-col gap-2">
      <div class="label flex justify-between">
        <label for="email">Email Address</label>
        <p v-if="formError.email" class="error-text">This field is required</p>
      </div>
      <Field
        name="email"
        type="email"
        placeholder="e.g. stephenking@lorem.com"
        class="input-field"
        v-model="formValue.email"
      ></Field>
    </div>
    <div class="form-group flex flex-col gap-2">
      <div class="label flex justify-between">
        <label for="phone">Phone Number</label>
        <p v-if="formError.phone" class="error-text">This field is required</p>
      </div>
      <Field
        name="phone"
        type="number"
        placeholder="e.g. +1 123456 3438"
        class="input-field"
        v-model="formValue.phone"
      ></Field>
    </div>
  </div>
</template>

<script setup>
import { inject } from "vue";
import { Field } from "vee-validate";

const { formValue, formError } = inject("state");
</script>
