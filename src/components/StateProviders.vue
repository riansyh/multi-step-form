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
    name: { status: false, message: "This field is required" },
    email: { status: false, message: "This field is required" },
    phone: { status: false, message: "This field is required" },
  },
});
provide("state", state);
</script>
