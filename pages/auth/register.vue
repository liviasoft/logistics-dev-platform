<script lang="ts" setup>
  import { toast } from '@neoncoder/vuetify-sonner'
  import { useDisplay } from 'vuetify'
  const { xlAndUp } = useDisplay()

  const onboardingSteps = ref([
  {
      icon: 'mdi-account-outline',
      title: 'Your details',
      subtitle: 'Provide an email and password',
      key: 'details',
      step: 1,
    },
    {
      icon: 'mdi-email-outline',
      title: 'Verify your email',
      subtitle: 'Enter your verification code',
      key: 'verify',
      step: 2,
    },
    {
      icon: 'mdi-account-multiple-outline',
      title: 'Invite your team',
      subtitle: 'Start collaborating with your team',
      key: 'team',
      step: 3,
    },
    {
      icon: 'mdi-rocket-launch-outline',
      title: 'Welcome to untitled',
      subtitle: 'Get up and running in 3 minutes',
      key: 'welcome',
      step: 4,
    }
  ])
  const activeStep = ref(1)
</script>

<template>
  <NuxtLayout name="process">
    <template #process-left>
      <div class="d-flex flex-column" style="min-height: calc(100vh - 64px); flex: 1;">
        <div>
          <div class="mt-0">
            <div>
              <VImg :src="'/images/LogoFull.svg'" :height="40" :width="200" class="mb-16"/>
            </div>
          <VTimeline density="comfortable" truncate-line="both">
            <VTimelineItem
              v-for="step in onboardingSteps"
              :key="step.key"
              align="start"
              class="mb-4"
              dot-color="pink"
              size="small"
             >
              <template #icon>
               
                <VCard :disabled="activeStep != step.step" :min-width="xlAndUp ? '50px': '40px'" :min-height="xlAndUp ? '50px': '40px'" class="rounded-lg d-flex align-center justify-center" border elevation="0" @click="() => {}">
                  <VIcon :class="activeStep != step.step ? 'text-disabled':''">{{ step.icon }}</VIcon>
                </VCard>
                
              </template>
              <div class="d-flex justify-space-between flex-grow-1">
                <div>
                  <p class="font-weight-bold text-high-emphasis" :class="{ 'text-disabled' : activeStep != step.step, 'text-h6' : xlAndUp, 'text-subtitle-1': !xlAndUp }">{{ step.title }}</p>
                  <p class="font-weight-light text-medium-emphasis text-subtitle-1 mt-n1" :class="{ 'text-disabled' : activeStep != step.step }">{{ step.subtitle }}</p>
                </div>
              </div>
            </VTimelineItem>
          </VTimeline>
          </div>
        </div>
        <VSpacer />
        <div class="d-flex align-center">
          <VBtn
          variant="text"
          prepend-icon="mdi-arrow-left"
          style="text-transform: none;"
          @click="toast('Event has been created', {
            description: 'Monday, January 3rd at 6:00pm',
          })">Back to home </VBtn>
          <VSpacer />
          <VBtn variant="text" class="text-capitalize">Sign In</VBtn>
        </div>
      </div>
    </template>
    <template #process-right>
      <div style="min-height: calc(100vh - 64px); flex: 1;">
        <VRow justify="center" class="pa-0 ma-0" style="height: 100%">
          <VCol lg="5" md="10" class="pa-0 ma-0">
            <div class="d-flex flex-column" style="height: 100%">
              <div>
                <div>
                  <VImg src="/images/Logomark.svg" height="40px" />
                </div>
                <div class="text-center mb-4">
                  <p class="text-h5 font-weight-bold mt-4">Create a free account</p>
                  <p class="text-subtitle-1">Provide your email and choose a password</p>
                </div>
                <p class="font-weight-bold">Email <span class="text-red">*</span></p>
                <v-text-field density="compact" placeholder="Enter your email" variant="outlined"/>
                <p class="font-weight-bold">Password <span class="text-red">*</span></p>
                <v-text-field density="compact" placeholder="Choose a password" variant="outlined"/>
                <div class="d-flex align-center pb-0">
                  <div v-for="(step, i) in onboardingSteps" :key="step.key" :class="{'mr-3': i < onboardingSteps.length - 1 }" class="rounded-lg bg-grey-lighten-2" style="height: 7px; flex: 1" />
                </div>
                <div class="d-flex align-center my-4">
                  <v-divider/>
                  <p class="px-8">OR</p>
                  <v-divider/>
                </div>
                <div>
                  <v-btn variant="flat" prepend-icon="mdi-google" border class="text-capitalize" style="text-transform: none;" :size="xlAndUp ? 'large': 'default'" rounded="lg" block>Sign up with Google</v-btn>
                  <v-btn variant="flat" class="bg-black mt-3" style="text-transform: none;" prepend-icon="mdi-github" :size="xlAndUp ? 'large': 'default'" rounded="lg" block>Sign up with Github</v-btn>
                  <v-btn variant="flat" class="bg-green-darken-4 mt-6" style="text-transform: none;" :size="xlAndUp ? 'large': 'default'" rounded="lg" block>Continue</v-btn>
                </div>
              </div>
              <VSpacer />
              <div class="d-flex align-center py-4">
                <div v-for="(step, i) in onboardingSteps" :key="step.key" class="rounded-lg" :class="{'mr-3': i < onboardingSteps.length - 1, 'bg-green-darken-4': step.step === activeStep,  'bg-grey-lighten-2': step.step !== activeStep }" style="height: 7px; flex: 1"/>
              </div>
            </div>
          </VCol>
        </VRow>
      </div>
    </template>
  </NuxtLayout>
</template>
