<template>
  <div class="flex flex-col px-6 py-5 rounded-lg bg-alabaster gap-6 fade-in">
    <div class="flex justify-between items-center">
      <div>
        <p class="font-semibold">{{ planName }} ({{ planType }})</p>
        <button
          class="text-sm underline text-cool-gray hover:text-purplish-blue transition-all"
          @click.prevent="() => (formState.index = 1)"
        >
          Change
        </button>
      </div>
      <p class="font-semibold">
        {{ planPrice }}
      </p>
    </div>
    <hr class="text-light-gray" v-if="formValue.addsOn.includes(true)" />
    <div class="flex justify-between" v-if="formValue.addsOn[0]">
      <p class="text-cool-gray text-sm">Online service</p>
      <p class="text-sm">+{{ addsOnPrice[0] }}</p>
    </div>
    <div class="flex justify-between" v-if="formValue.addsOn[1]">
      <p class="text-cool-gray text-sm">Larger storage</p>
      <p class="text-sm">+{{ addsOnPrice[1] }}</p>
    </div>
    <div class="flex justify-between" v-if="formValue.addsOn[2]">
      <p class="text-cool-gray text-sm">Customizable profile</p>
      <p class="text-sm">+{{ addsOnPrice[2] }}</p>
    </div>
  </div>
  <div class="flex justify-between px-6 py-5 rounded-lg gap-6 fade-in">
    <p class="text-cool-gray">
      Total (per {{ formValue.plan.type.split("ly")[0] }})
    </p>
    <p class="text-lg font-bold text-purplish-blue">{{ totalPrice }}</p>
  </div>
</template>

<script setup>
import { inject, computed } from "vue";
import { addsOn } from "../assets/data/adds-on";
import { useCapitalFirstLetter } from "../utils/capital-first-letter";
const { formValue, formState } = inject("state");

const planName = computed(() => useCapitalFirstLetter(formValue.plan.name));
const planType = computed(() => useCapitalFirstLetter(formValue.plan.type));
const planPrice = computed(
  () =>
    `$${formValue.plan.price}/${formValue.plan.type === "yearly" ? "yr" : "mo"}`
);

const addsOnPrice = computed(() => {
  const prices = addsOn.map((adds) => adds.price);
  const month = formValue.plan.type === "monthly" ? 1 : 10;
  const type = formValue.plan.type === "monthly" ? "mo" : "yr";

  const result = prices.map((price) => {
    return `$${parseInt(price) * month}/${type}`;
  });

  return result;
});

const totalPrice = computed(() => {
  const type = formValue.plan.type === "monthly" ? "mo" : "yr";
  const month = formValue.plan.type === "monthly" ? 1 : 10;
  const planPrice = formValue.plan.price;
  let addsOnPrice = 0;

  if (formValue.addsOn[0]) addsOnPrice += 1 * month;
  if (formValue.addsOn[1]) addsOnPrice += 2 * month;
  if (formValue.addsOn[2]) addsOnPrice += 2 * month;

  return `$${parseInt(planPrice + addsOnPrice)}/${type}`;
});
</script>
