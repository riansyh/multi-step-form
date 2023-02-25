<template>
  <label
    :for="id"
    class="plan-card"
    :class="{ 'plan-card-active': formValue.plan.name === props.name }"
  >
    <Field
      type="radio"
      name="plan"
      :id="id"
      :value="props.name"
      v-model="formValue.plan['name']"
      class="hidden"
    ></Field>
    <div class="w-10 h-10 rounded-full bg-purplish-blue">
      <img :src="imgUrl" :alt="props.name" />
    </div>
    <div>
      <h3 class="font-semibold">{{ name }}</h3>
      <p class="text-xs text-cool-gray">{{ price(props.price) }}</p>
      <p class="mt-1 text-xs" v-if="formValue.plan.type === 'yearly'">
        2 months free
      </p>
    </div>
  </label>
</template>

<script setup>
import { Field } from "vee-validate";
import { inject, computed } from "vue";
import { useCapitalFirstLetter } from "../../utils/capital-first-letter";

const { formValue } = inject("state");
const props = defineProps({
  name: String,
  price: String,
});

const imgUrl = computed(() => `/icon-${props.name}.svg`);

const id = computed(() => `plan-${props.name}`);

const name = computed(() => useCapitalFirstLetter(props.name));

const price = computed(() => {
  return (price) => {
    const month = formValue.plan.type === "monthly" ? 1 : 10;
    const type = formValue.plan.type === "monthly" ? "mo" : "yr";
    const priceText = `$${parseInt(price) * month}/${type}`;
    formValue.plan.price = priceText;

    return priceText;
  };
});
</script>
