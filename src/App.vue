<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router';
import CustomShapeButton from '@/components/CustomShapeButton.vue';
import DashboardSidebarMenu from '@/components/DashboardSidebarMenu.vue';
</script>

<template>
  <header>
    <div class="wrapper">
      <CustomShapeButton></CustomShapeButton>
      <DashboardSidebarMenu></DashboardSidebarMenu>
    </div>
  </header>

</template>

