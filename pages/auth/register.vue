<script lang="ts" setup>
  import { toast } from '@neoncoder/vuetify-sonner'

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
          <div class="mt-16 pt-16">
          <VTimeline density="compact" truncate-line="both">
            <VTimelineItem
              v-for="step in onboardingSteps"
              :key="step.key"
              align="start"
              class="mb-4"
              dot-color="pink"
              size="small"
             >
              <template #icon>
               
                <VCard :disabled="activeStep != step.step" min-width="36px" min-height="36px" class="rounded-lg d-flex align-center justify-center" border elevation="0" @click="() => {}">
                  <VIcon :class="activeStep != step.step ? 'text-disabled':''">{{ step.icon }}</VIcon>
                </VCard>
                
              </template>
              <div class="d-flex justify-space-between flex-grow-1">
                <div>
                  <p class="font-weight-bold text-subtitle-2" :class="activeStep != step.step ? 'text-disabled':''">{{ step.title }}</p>
                  <p class="font-weight-light text-subtitle-2" :class="activeStep != step.step ? 'text-disabled':''">{{ step.subtitle }}</p>
                </div>
              </div>
            </VTimelineItem>
            <!-- <VTimelineItem
              class="mb-4"
              dot-color="pink"
              size="small"
             >
              <template #icon>
                <VCard :disabled="true" min-width="40px" min-height="40px" class="rounded-lg d-flex align-center justify-center" border elevation="0" @click="() => {}">
                  <VIcon color="grey">mdi-email-outline</VIcon>
                </VCard>
              </template>
              <div class="d-flex justify-space-between flex-grow-1">
                <div>
                  <p class="font-weight-bold text-disabled">Verify your email</p>
                  <p class="font-weight-light text-disabled">Enter your verification code</p>
                </div>
              </div>
            </VTimelineItem> -->
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
      <div class="d-flex flex-column" style="min-height: calc(100vh - 64px); flex: 1;">
        RIGHT
      </div>
    </template>
  </NuxtLayout>
</template>
