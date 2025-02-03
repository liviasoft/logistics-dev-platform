<script lang="ts" setup>
  import { toast } from '@neoncoder/vuetify-sonner'
</script>

<template>
  <NuxtLayout name="process">
    <template #process-left>
      <div class="d-flex flex-column" style="min-height: calc(100vh - 64px); flex: 1;">
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
