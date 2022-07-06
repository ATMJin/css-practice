<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router';
import CustomShapeButton from '@/components/CustomShapeButton.vue';
import DashboardSidebarMenu from '@/components/DashboardSidebarMenu.vue';
import VanillaJavascriptParticles from '@/components/VanillaJavascriptParticles.vue';
</script>

<template>
  <header>
    <div class="wrapper">
      <DashboardSidebarMenu></DashboardSidebarMenu>
      <!-- <VanillaJavascriptParticles></VanillaJavascriptParticles> -->
    </div>
  </header>

</template>

