<script lang="ts" setup>
  import { useDisplay } from 'vuetify'
  const { xlAndUp, mdAndUp } = useDisplay()
</script>

<template>
  <div>
    <div class="text-center mb-4">
      <p class="text-h5 font-weight-bold mt-4">Verify your email</p>
      <p class="text-subtitle-1">We sent a code to <strong>your@email.com</strong></p>
    </div>
    <div style="width: 100%;" class="text-center">
      <VOtpInput :length="4" height="100px" :min-width="mdAndUp ? '400px': '200px'"/>
      <p>Didn't get a code? <strong class="text-decoration-underline" style="cursor: pointer;">Click to resend</strong></p>
    </div>
    <div>
      <v-btn variant="flat" class="bg-green-darken-4 mt-6" style="text-transform: none;" :size="xlAndUp ? 'large': 'default'" rounded="lg" block>Continue</v-btn>
    </div>
  </div>
</template>

<style lang="postcss" scoped>
  
</style>
