<template>
  <StepperComponent
    class="md:hidden flex top-0 left-0 right-0 fixed md:relative pb-24"
  />
  <section
    class="min-w-[80vw] md:min-w-fit md:max-w-[940px] max-h-[600px] lg:min-h-[600px] bg-white p-4 rounded-[16px] flex flex-col md:flex-row shadow-blue z-30 mt-24 md:mt-0 mb-32 md:mb-0"
  >
    <StepperComponent class="hidden md:flex" />

    <div
      class="form-container flex-grow px-6 md:px-10 lg:px-[100px] py-[18px] flex flex-col justify-between md:w-[400px] lg:min-w-[650px]"
    >
      <div class="form-header" v-if="!isFinished">
        <h2 class="text-4xl font-bold">{{ title[formState.index].title }}</h2>
        <p class="mt-2 mb-10 text-cool-gray">
          {{ title[formState.index].desc }}
        </p>

        <Form class="form">
          <FirstForm v-if="formState.index === 0" />
          <SecondForm v-else-if="formState.index === 1" />
          <ThirdForm v-else-if="formState.index === 2" />
          <FourthForm v-else-if="formState.index === 3" />
        </Form>
      </div>
      <div
        class="form-footer flex w-full justify-between items-end fixed md:relative bg-white left-0 bottom-0 p-4 md:p-0 mt-10"
        v-if="!isFinished"
      >
        <button
          :class="{ invisible: formState.index === 0 }"
          class="button text-cool-gray hover:text-marine-blue px-0"
          @click="handleBack"
        >
          Go Back
        </button>
        <button
          class="bg-marine-blue hover:bg-purplish-blue button"
          @click="handleNext"
          v-if="formState.index < 3"
        >
          Next Step
        </button>
        <button
          class="bg-purplish-blue hover:bg-opacity-75 button"
          @click="() => (isFinished = true)"
          v-if="formState.index === 3"
        >
          Confirm
        </button>
      </div>

      <ThankYouView v-if="isFinished" />
    </div>
  </section>

  <div class="text-center py-4">
    <p>
      Challenge by
      <a
        class="font-semibold text-purplish-blue"
        href="https://www.frontendmentor.io?ref=challenge"
        target="_blank"
        >Frontend Mentor</a
      >. Coded by
      <a class="font-semibold text-purplish-blue" href="https://riansyh.tech/"
        >Rian Febriansyah</a
      >.
    </p>
  </div>
</template>

<script setup>
import { inject, ref, defineAsyncComponent } from "vue";
import { title } from "./../assets/data/title";
import { Form } from "vee-validate";
import StepperComponent from "./StepperComponent.vue";
import FirstForm from "./FirstForm.vue";

const SecondForm = defineAsyncComponent(() => import("./SecondForm.vue"));
const ThirdForm = defineAsyncComponent(() => import("./ThirdForm.vue"));
const FourthForm = defineAsyncComponent(() => import("./FourthForm.vue"));
const ThankYouView = defineAsyncComponent(() => import("./ThankYouView.vue"));

const { formState, formError, formValue } = inject("state");
const isFinished = ref(false);

const testEmailFormat = (email) => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);

const handleNext = () => {
  if (formState.index === 0) {
    if (formValue.name === "") {
      formError.name.status = true;
    } else {
      formError.name.status = false;
    }

    if (formValue.email === "" || !testEmailFormat(formValue.email)) {
      formError.email.status = true;
      if (!testEmailFormat(formValue.email) && formValue.email !== "") {
        formError.email.message = "Email format invalid";
      } else {
        formError.email.message = "This field is required";
      }
    } else {
      formError.email.status = false;
    }

    if (formValue.phone === "") {
      formError.phone.status = true;
    } else {
      formError.phone.status = false;
    }

    if (
      formError.name.status ||
      formError.email.status ||
      formError.phone.status
    )
      return;

    formState.index += 1;
  } else if (formState.index < 4) formState.index += 1;
};

const handleBack = () => {
  if (formState.index > 0) formState.index -= 1;
};
</script>
