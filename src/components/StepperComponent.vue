<template>
  <div
    class="steper p-10 md:rounded-lg bg-purplish-blue flex md:flex-col gap-3 md:gap-8 items-start justify-center md:justify-start md:min-w-[274px] md:min-h-[568px] md:relative overflow-hidden"
  >
    <StepItem
      v-for="(title, index) in titles"
      :key="`adds-${index}`"
      :title="title"
      :index="index"
    />

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
import StepItem from "./StepItem.vue";

const titles = ["your info", "select plan", "adds-on", "summary"];
</script>
