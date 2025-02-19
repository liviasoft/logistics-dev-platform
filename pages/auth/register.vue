<script lang="ts" setup>
  import CreateAccountSection from '../../components/sections/CreateAccountSection.vue'
  import VerifyEmailSection from '../../components/sections/VerifyEmailSection.vue'
  import TeamDetailsSection from '../../components/sections/TeamDetailsSection.vue'
  import OnboardingCompleteSection from '../../components/sections/OnboardingCompleteSection.vue'
  import { toast } from '@neoncoder/vuetify-sonner'
  import { useDisplay } from 'vuetify'
  import type { OnboardingStep } from '~/types/onboarding.types';
  const { xlAndUp, mdAndUp } = useDisplay()

  const onboardingSteps = ref<OnboardingStep[]>([
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
  const activeStep = ref(4)
</script>

<template>
  <NuxtLayout name="process">
    <template #process-left>
      <div class="d-flex flex-column" style="min-height: calc(100vh - 64px); flex: 1;">
        <div>
          <div class="mt-0">
            <div>
              <VImg :src="'/images/LogoFull.svg'" :height="40" :width="200" :class="{ 'mb-16': mdAndUp, 'mb-4': !mdAndUp }"/>
            </div>
            <div style="display: flex; justify-content: center;">
              <VTimeline :density="mdAndUp ? 'comfortable' : 'compact'" align="start" truncate-line="both">
                <VTimelineItem
                  v-for="step in onboardingSteps"
                  :key="step.key"
                  
                  class="mb-4"
                  dot-color="pink"
                  size="small"
                >
                  <template #icon>
                    <VCard :disabled="activeStep != step.step" :min-width="xlAndUp ? '50px': '40px'" :min-height="xlAndUp ? '50px': '40px'" class="rounded-lg d-flex align-center justify-center mt-4" border elevation="0" @click="() => {}">
                      <VIcon :class="activeStep != step.step ? 'text-disabled':''">{{ step.icon }}</VIcon>
                    </VCard>
                  </template>
                  <div>
                    <div>
                      <p class="font-weight-bold text-high-emphasis" :class="{ 'text-disabled' : activeStep != step.step, 'text-h6' : xlAndUp, 'text-subtitle-1': !xlAndUp }">{{ step.title }}</p>
                      <p class="font-weight-light text-medium-emphasis text-subtitle-1 mt-n1" :class="{ 'text-disabled' : activeStep != step.step }">{{ step.subtitle }}</p>
                      <div v-if="!mdAndUp">
                        <VExpandTransition>
                          <div v-show="activeStep === step.step">
                            <CreateAccountSection v-if="step.step === 1" :onboarding-steps="onboardingSteps"/>
                            <VerifyEmailSection v-if="step.step === 2" />
                            <TeamDetailsSection v-if="step.step === 3" />
                            <OnboardingCompleteSection v-if="step.step === 4" />
                          </div>
                        </VExpandTransition>
                      </div>
                    </div>
                  </div>
                </VTimelineItem>
              </VTimeline>
            </div>
          </div>
        </div>
        <VSpacer />
        <div class="d-flex align-center" :class="{ 'mt-4': !mdAndUp }">
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
                <VWindow v-model="activeStep">
                  <VWindowItem :value="1">
                    <CreateAccountSection :onboarding-steps="onboardingSteps" />
                  </VWindowItem>
                  <VWindowItem :value="2">
                    <VerifyEmailSection />
                  </VWindowItem>
                  <VWindowItem :value="3">
                    <TeamDetailsSection />
                  </VWindowItem>
                  <VWindowItem :value="4">
                    <OnboardingCompleteSection />
                  </VWindowItem>
                </VWindow>
              </div>
              <VSpacer />
              <div class="d-flex align-center py-4">
                <div v-for="(step, i) in onboardingSteps" :key="step.key" class="rounded-lg" :class="{'mr-3': i < onboardingSteps.length - 1, 'bg-green-darken-4': step.step === activeStep,  'bg-grey-lighten-2': step.step !== activeStep }" style="height: 7px; flex: 1" @click="activeStep = i + 1"/>
              </div>
            </div>
          </VCol>
        </VRow>
      </div>
    </template>
  </NuxtLayout>
</template>
<style>
  .v-otp-input__field {
    font-size: 3em;
  }
</style>
