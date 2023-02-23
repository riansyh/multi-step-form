<template>
  <div class="flex flex-col gap-8 w-full">
    <div class="flex flex-row justify-between w-full gap-8">
      <label
        for="plan-1"
        class="plan-card"
        :class="{ 'plan-card-active': formValue.plan.name === 'arcade' }"
      >
        <Field
          type="radio"
          name="plan"
          id="plan-1"
          value="arcade"
          v-model="formValue.plan['name']"
          class="hidden"
        ></Field>
        <div class="w-10 h-10 rounded-full bg-purplish-blue">
          <img src="./../assets/images/icon-arcade.svg" alt="arcade icon" />
        </div>
        <div>
          <h3 class="font-semibold">Arcade</h3>
          <p class="text-xs text-cool-gray">{{ price(9) }}</p>
          <p class="mt-1 text-xs" v-if="formValue.plan.type === 'yearly'">
            2 months free
          </p>
        </div>
      </label>
      <label
        for="plan-2"
        class="plan-card"
        :class="{ 'plan-card-active': formValue.plan.name === 'advanced' }"
      >
        <Field
          type="radio"
          name="plan"
          id="plan-2"
          value="advanced"
          v-model="formValue.plan['name']"
          class="hidden"
        ></Field>
        <div class="w-10 h-10 rounded-full bg-purplish-blue">
          <img src="./../assets/images/icon-advanced.svg" alt="advanced icon" />
        </div>
        <div>
          <h3 class="font-semibold">Advanced</h3>
          <p class="text-xs text-cool-gray">{{ price(12) }}</p>
          <p class="mt-1 text-xs" v-if="formValue.plan.type === 'yearly'">
            2 months free
          </p>
        </div>
      </label>
      <label
        for="plan-3"
        class="plan-card"
        :class="{ 'plan-card-active': formValue.plan.name === 'pro' }"
      >
        <Field
          type="radio"
          name="plan"
          id="plan-3"
          value="pro"
          v-model="formValue.plan['name']"
          class="hidden"
        ></Field>
        <div class="w-10 h-10 rounded-full bg-purplish-blue">
          <img src="./../assets/images/icon-pro.svg" alt="pro icon" />
        </div>
        <div>
          <h3 class="font-semibold">Pro</h3>
          <p class="text-xs text-cool-gray">{{ price(15) }}</p>
          <p class="mt-1 text-xs" v-if="formValue.plan.type === 'yearly'">
            2 months free
          </p>
        </div>
      </label>
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
      <div class="p-1 rounded-full w-10 bg-marine-blue transition-all">
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
import { inject, computed } from "vue";

const { formValue } = inject("state");

const price = computed(() => {
  return (price) => {
    const month = formValue.plan.type === "monthly" ? 1 : 10;
    const type = formValue.plan.type === "monthly" ? "mo" : "yr";
    return `$${parseInt(price) * month}/${type}`;
  };
});
</script>
