<template>
  <div class="flex flex-col gap-3 fade-in">
    <AddsOnCard
      v-for="(adds, index) in addsOn"
      :title="adds.title"
      :desc="adds.desc"
      :price="adds.price"
      :index="index"
      :key="`adds-${index}`"
    />
  </div>
</template>

<script setup>
import AddsOnCard from "./parts/AddsOnCard.vue";
import { addsOn } from "../assets/data/adds-on";
</script>
