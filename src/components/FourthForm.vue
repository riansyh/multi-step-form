<template>
  <div class="flex flex-col px-6 py-5 rounded-lg bg-alabaster gap-6">
    <div class="flex justify-between items-center">
      <div>
        <p class="font-semibold">Aracade (Monthly)</p>
        <button
          class="text-sm underline text-cool-gray hover:text-purplish-blue transition-all"
        >
          Change
        </button>
      </div>
      <p class="font-semibold">$9/mo</p>
    </div>
    <hr class="text-light-gray" />
    <div class="flex justify-between">
      <p class="text-cool-gray text-sm">Online service</p>
      <p class="text-sm">+1$/mo</p>
    </div>
    <div class="flex justify-between">
      <p class="text-cool-gray text-sm">Larger storage</p>
      <p class="text-sm">+2$/mo</p>
    </div>
    <div class="flex justify-between">
      <p class="text-cool-gray text-sm">Customizable profile</p>
      <p class="text-sm">+2$/mo</p>
    </div>
  </div>
</template>

<script setup>
import { inject } from "vue";

const { formValue } = inject("state");
</script>
