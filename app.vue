<script lang="ts" setup>
  import { VSonner } from '@neoncoder/vuetify-sonner'
  import '@neoncoder/vuetify-sonner/style.css'
</script>
<template>
  <div>
    <NuxtRouteAnnouncer />
    <!-- <NuxtLayout> -->
      <NuxtPage />
    <!-- </NuxtLayout> -->
    <VSonner position="bottom-right" :visible-toasts="3" :expand="false" />
    <!-- <VBtn
      @click="toast('Event has been created', {
        description: 'Monday, January 3rd at 6:00pm',
      })">Here is a button</VBtn>
    <NuxtWelcome /> -->
  </div>
</template>
