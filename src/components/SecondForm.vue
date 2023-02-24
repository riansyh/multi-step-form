<template>
  <div class="flex flex-col gap-8 w-full fade-in">
    <div
      class="flex md:flex-row flex-col justify-between w-full gap-3 md:gap-4 lg:gap-8"
    >
      <PlanCard name="arcade" price="9" />
      <PlanCard name="advanced" price="12" />
      <PlanCard name="pro" price="15" />
    </div>
    <div
      class="flex items-center justify-center p-3 rounded-lg w-full gap-6 bg-alabaster"
    >
      <label
        for="monthly"
        class="font-semibold cursor-pointer"
        :class="{ 'text-light-gray': formValue.plan.type == 'yearly' }"
      >
        Monthly
        <Field
          type="radio"
          name="type"
          value="monthly"
          id="monthly"
          class="hidden"
          v-model="formValue.plan.type"
        />
      </label>
      <div
        class="p-1 rounded-full w-10 bg-marine-blue transition-all cursor-pointer"
        @click="handleToggle"
      >
        <div
          class="w-3 h-3 bg-white rounded-full transition-all"
          :class="
            formValue.plan.type == 'yearly' ? 'translate-x-5' : 'translate-x-0'
          "
        ></div>
      </div>
      <label
        for="yearly"
        class="font-semibold cursor-pointer"
        :class="{ 'text-light-gray': formValue.plan.type == 'monthly' }"
      >
        Yearly
        <Field
          type="radio"
          name="type"
          value="yearly"
          id="yearly"
          class="hidden"
          v-model="formValue.plan.type"
        />
      </label>
    </div>
  </div>
</template>

<script setup>
import { Field } from "vee-validate";
import { inject, watch } from "vue";
import { price } from "../assets/data/price";
import PlanCard from "./PlanCard.vue";

const { formValue } = inject("state");

const handleToggle = () => {
  if (formValue.plan.type === "monthly") {
    formValue.plan.type = "yearly";
  } else {
    formValue.plan.type = "monthly";
  }
};

watch(formValue.plan, () => {
  const month = formValue.plan.type === "monthly" ? 1 : 10;
  formValue.plan.price = price[formValue.plan.name] * month;
});
</script>
