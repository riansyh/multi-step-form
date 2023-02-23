<template>
  <section
    class="max-w-[940px] max-h-[600px] md:min-h-[600px] bg-white p-4 rounded-[16px] flex flex-col md:flex-row shadow-blue"
  >
    <div
      class="steper p-10 rounded-lg bg-purplish-blue flex items-start justify-start md:min-w-[274px]"
    >
      <div class="flex flex-row gap-4 items-center">
        <div
          class="px-3 py-2 h-fit leading-none rounded-full border-[1px] border-light-gray text-light-gray"
        >
          1
        </div>
        <div>
          <p class="leading-tight text-light-gray text-opacity-90">STEP 1</p>
          <p class="stepper-title">YOUR INFO</p>
        </div>
      </div>
    </div>
    <div
      class="form-container flex-grow px-[100px] py-[18px] flex flex-col justify-between md:min-w-[450px]"
    >
      <div class="form-header">
        <h2 class="text-4xl font-bold">{{ title[formState].title }}</h2>
        <p class="mb-10 text-cool-gray">{{ title[formState].desc }}</p>

        <!-- form goes here -->
        <Form class="form flex flex-col gap-6">
          <div class="form-group flex flex-col gap-2">
            <div class="label flex justify-between">
              <label for="name">Name</label>
              <p class="error-text">This file is</p>
            </div>
            <Field
              name="name"
              type="text"
              placeholder="e.g. Stephen King"
              class="input-field"
            ></Field>
          </div>
          <div class="form-group flex flex-col gap-2">
            <div class="label flex justify-between">
              <label for="email">Email Address</label>
              <p class="error-text">This file is</p>
            </div>
            <Field
              name="email"
              type="email"
              placeholder="e.g. stephenking@lorem.com"
              class="input-field"
            ></Field>
          </div>
          <div class="form-group flex flex-col gap-2">
            <div class="label flex justify-between">
              <label for="phone">Phone Number</label>
              <p class="error-text">This file is</p>
            </div>
            <Field
              name="phone"
              type="number"
              placeholder="e.g. +1 123456 3438"
              class="input-field"
            ></Field>
          </div>
        </Form>
      </div>
      <div class="form-footer flex w-full justify-between items-end">
        <button class="button text-cool-gray hover:text-marine-blue">
          Go Back
        </button>
        <button class="bg-marine-blue hover:bg-purplish-blue button">
          Next Step
        </button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { inject } from "vue";
import { title } from "./../assets/data/title";
import { Form, Field } from "vee-validate";

const { formState } = inject("state");
</script>
