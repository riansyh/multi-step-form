<template>
  <div class="flex flex-col gap-6 fade-in">
    <InputField name="name" placeholder="e.g. Stephen King" type="text" />
    <InputField
      name="email"
      placeholder="e.g. stephenking@lorem.com"
      type="email"
    />
    <InputField name="phone" placeholder="e.g. +1 123456 3438" type="number" />
  </div>
</template>

<script setup>
import InputField from "./InputField.vue";
</script>
