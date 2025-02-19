<script lang="ts" setup>
import type { OnboardingStep } from '~/types/onboarding.types';
import { useDisplay } from 'vuetify'
const { xlAndUp } = useDisplay()

const props = defineProps({
  onboardingSteps: {
    type: Array as () => OnboardingStep[],
    required: true,
    default: () => ([])
  }
})
</script>

<template>
  <div>
    <div class="text-center mb-4">
      <p class="text-h5 font-weight-bold mt-4">Create a free account</p>
      <p class="text-subtitle-1">Provide your email and choose a password</p>
    </div>
    <p class="font-weight-bold">Email <span class="text-red">*</span></p>
    <v-text-field density="compact" placeholder="Enter your email" variant="outlined" />
    <p class="font-weight-bold">Password <span class="text-red">*</span></p>
    <v-text-field density="compact" type="password" placeholder="Choose a password" variant="outlined" />
    <div class="d-flex align-center pb-0">
      <div
v-for="(step, i) in props.onboardingSteps" :key="step.key"
        :class="{ 'mr-3': i < props.onboardingSteps.length - 1 }" class="rounded-lg bg-grey-lighten-2"
        style="height: 7px; flex: 1" />
    </div>
    <div class="d-flex align-center my-4">
      <v-divider />
      <p class="px-8">OR</p>
      <v-divider />
    </div>
    <div>
      <v-btn
variant="flat" :disabled="false" :loading="false" prepend-icon="mdi-google" border class="text-capitalize"
        style="text-transform: none;" :size="xlAndUp ? 'large' : 'default'" rounded="lg" block>Sign up with
        Google</v-btn>
      <v-btn
variant="flat" :disabled="false" :loading="false" class="bg-black mt-3" style="text-transform: none;"
        prepend-icon="mdi-github" :size="xlAndUp ? 'large' : 'default'" rounded="lg" block>Sign up with Github</v-btn>
      <v-btn
variant="flat" :disabled="false" :loading="false" class="bg-green-darken-4 mt-6"
        style="text-transform: none;" :size="xlAndUp ? 'large' : 'default'" rounded="lg" block>Continue</v-btn>
    </div>
  </div>
</template>
