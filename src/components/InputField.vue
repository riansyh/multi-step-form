<template>
  <div class="form-group flex flex-col gap-2">
    <div class="form-label">
      <label :for="props.name">{{ title }}</label>
      <p v-if="formError[props.name].status" class="error-text">
        {{ formError[props.name].message }}
      </p>
    </div>
    <Field
      :name="props.name"
      :type="props.type"
      :placeholder="props.placeholder"
      class="input-field"
      :class="{ error: formError[props.name].status }"
      v-model="formValue[props.name]"
    ></Field>
  </div>
</template>

<script setup>
import { inject, computed } from "vue";
import { Field } from "vee-validate";
import { useCapitalFirstLetter } from "../utils/capital-first-letter";

const { formValue, formError } = inject("state");
const props = defineProps({
  name: String,
  type: String,
  placeholder: String,
});

const title = computed(() => useCapitalFirstLetter(props.name));
</script>
