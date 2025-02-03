<script lang="ts" setup>
  import { VSonner, toast } from '@neoncoder/vuetify-sonner'
  import '@neoncoder/vuetify-sonner/style.css'
</script>
<template>
  <div>
    <NuxtRouteAnnouncer />
    <VSonner position="bottom-left" :visible-toasts="5" :expand="false" />
    <VBtn @click="toast('My first toast')">Here is a button</VBtn>
    <h1>Hello World</h1>
    <NuxtWelcome />
  </div>
</template>
