<template>
  <div
    class="steper p-10 md:rounded-lg bg-purplish-blue flex md:flex-col gap-3 md:gap-8 items-start justify-center md:justify-start md:min-w-[274px] md:min-h-[568px] md:relative overflow-hidden"
  >
    <div class="flex flex-row gap-4 items-center z-10">
      <div
        class="stepper-num"
        :class="{ 'stepper-num-active': formState.index === 0 }"
      >
        1
      </div>
      <div class="hidden md:block">
        <p class="leading-tight text-light-gray text-opacity-90">STEP 1</p>
        <p class="stepper-title">YOUR INFO</p>
      </div>
    </div>
    <div class="flex flex-row gap-4 items-center z-10">
      <div
        class="stepper-num"
        :class="{ 'stepper-num-active': formState.index === 1 }"
      >
        2
      </div>
      <div class="hidden md:block">
        <p class="leading-tight text-light-gray text-opacity-90">STEP 2</p>
        <p class="stepper-title">SELECT PLAN</p>
      </div>
    </div>
    <div class="flex flex-row gap-4 items-center z-10">
      <div
        class="stepper-num"
        :class="{ 'stepper-num-active': formState.index === 2 }"
      >
        3
      </div>
      <div class="hidden md:block">
        <p class="leading-tight text-light-gray text-opacity-90">STEP 3</p>
        <p class="stepper-title">ADDS-ON</p>
      </div>
    </div>
    <div class="flex flex-row gap-4 items-center z-10">
      <div
        class="stepper-num"
        :class="{ 'stepper-num-active': formState.index === 3 }"
      >
        4
      </div>
      <div class="hidden md:block">
        <p class="leading-tight text-light-gray text-opacity-90">STEP 4</p>
        <p class="stepper-title">SUMMARY</p>
      </div>
    </div>
    <img
      src="./../assets/images/bg-sidebar-desktop.svg"
      alt=""
      class="absolute top-0 left-0 z-[1] hidden md:block"
    />
    <img
      src="./../assets/images/bg-sidebar-mobile.svg"
      alt=""
      class="absolute bottom-0 left-0 z-[1] md:hidden block w-full self-end"
    />
  </div>
</template>

<script setup>
import { inject } from "vue";
const { formState } = inject("state");
</script>
