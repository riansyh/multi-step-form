<template>
  <div class="flex flex-col gap-3 fade-in">
    <label
      for="adds-1"
      class="addson-card"
      :class="{ 'addson-card-active': formValue.addsOn[0] == 'true' }"
    >
      <div class="flex gap-6">
        <Field
          v-model="formValue.addsOn[0]"
          name="adds-1"
          type="checkbox"
          value="true"
          id="adds-1"
        />
        <div>
          <p class="font-semibold">Online service</p>
          <p class="text-xs text-cool-gray">Access to multiplayer games</p>
        </div>
      </div>
      <p class="text-purplish-blue">+$1/mo</p>
    </label>
    <label
      for="adds-2"
      class="addson-card"
      :class="{ 'addson-card-active': formValue.addsOn[1] == 'true' }"
    >
      <div class="flex gap-6">
        <Field
          v-model="formValue.addsOn[1]"
          name="adds-2"
          type="checkbox"
          value="true"
          id="adds-2"
        />
        <div>
          <p class="font-semibold">Larger storage</p>
          <p class="text-xs text-cool-gray">Extra 1TB of cloud save</p>
        </div>
      </div>
      <p class="text-purplish-blue">+$2/mo</p>
    </label>
    <label
      for="adds-3"
      class="addson-card"
      :class="{ 'addson-card-active': formValue.addsOn[2] == 'true' }"
    >
      <div class="flex gap-6">
        <Field
          v-model="formValue.addsOn[2]"
          name="adds-3"
          type="checkbox"
          value="true"
          id="adds-3"
        />
        <div>
          <p class="font-semibold">Customizable Profile</p>
          <p class="text-xs text-cool-gray">Access to multiplayer games</p>
        </div>
      </div>
      <p class="text-purplish-blue">+$2/mo</p>
    </label>
  </div>
</template>

<script setup>
import { Field } from "vee-validate";
import { inject } from "vue";

const { formValue } = inject("state");
</script>
