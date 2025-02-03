<script lang="ts" setup>
  import { useDisplay } from 'vuetify'
  const { mdAndUp, lgAndUp, mdAndDown } = useDisplay()
</script>

<template>
  <VApp>
    <VMain>
      <div class="d-flex" style="width: 100vw; height: 100vh;">
        <div :style="{ width: mdAndDown ? '100vw' : lgAndUp ? '30vw' : '45vw' }" style="height: 100vh; background-color: #FAFAFA; background-image: url('/images/Logomark.svg'); background-position: bottom 40px right -100px; background-size: 300px;">
          <VContainer min-height="100%" class="px-8 py-8 d-flex" style="backdrop-filter: blur(2px); background-color: #FAFAFAEE;">
            <slot name="process-left" />
          </VContainer>
        </div>
        <div v-if="mdAndUp" style="height: 100vh;">
          <div :style="{ width: lgAndUp ? '70vw' : '55vw' }">
            <VContainer min-height="100%" class="px-8 py-8 d-flex">
              <slot name="process-right" />
            </VContainer>
          </div>
        </div>
      </div>
    </VMain>
  </VApp>
</template>
