<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router';
import MagicVerticalTabMenu from '@/components/MagicVerticalTabMenu.vue';
import CurveOutsideEffects from '@/components/CurveOutsideEffects.vue';
</script>

<template>
  <header>
    <div class="wrapper">
      <MagicVerticalTabMenu></MagicVerticalTabMenu>
      <CurveOutsideEffects></CurveOutsideEffects>
    </div>
  </header>

</template>

