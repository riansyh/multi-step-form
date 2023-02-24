<template>
  <label
    :for="id"
    class="addson-card"
    :class="{ 'addson-card-active': formValue.addsOn[props.index] == 'true' }"
  >
    <div class="flex gap-6">
      <Field
        v-model="formValue.addsOn[props.index]"
        :name="id"
        type="checkbox"
        value="true"
        :id="id"
      />
      <div>
        <p class="font-semibold">{{ props.title }}</p>
        <p class="text-xs text-cool-gray">{{ props.desc }}</p>
      </div>
    </div>
    <p class="text-purplish-blue">+${{ props.price }}/mo</p>
  </label>
</template>

<script setup>
import { Field } from "vee-validate";
import { inject, computed } from "vue";

const { formValue } = inject("state");

const props = defineProps({
  title: String,
  desc: String,
  price: Number,
  index: Number,
});

const id = computed(() => `adds-${props.index}`);
</script>
