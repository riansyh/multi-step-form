<template>
  <div class="flex flex-row gap-4 items-center z-10">
    <div
      class="stepper-num"
      :class="{ 'stepper-num-active': formState.index === props.index }"
    >
      {{ props.index + 1 }}
    </div>
    <div class="hidden md:block">
      <p class="leading-tight text-light-gray text-opacity-90">
        STEP {{ props.index + 1 }}
      </p>
      <p class="stepper-title uppercase">{{ props.title }}</p>
    </div>
  </div>
</template>

<script setup>
import { inject, defineProps } from "vue";

const { formState } = inject("state");

const props = defineProps({
  title: String,
  index: Number,
});
</script>
