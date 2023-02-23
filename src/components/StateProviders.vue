<template>
  <slot />
</template>

<script setup>
import { provide, reactive } from "vue";

const state = reactive({
  formValue: {
    name: "",
    email: "",
    phone: "",
    plan: {
      name: "arcade",
      type: "monthly",
      price: "",
    },
    addsOn: [false, false, false],
  },
  formState: { index: 0 },
  formError: {
    name: false,
    email: false,
    phone: false,
  },
});
provide("state", state);
</script>
