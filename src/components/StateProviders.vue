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
    },
    addsOn: [false, false, false],
  },
  formState: { index: 0 },
});
provide("state", state);
</script>
