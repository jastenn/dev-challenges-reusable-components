<template>
  <div class="app">
    <TheSidebar />
    <div class="col-2 main">
      <router-view />
    </div>
  </div>
</template>

<script setup lang="ts">
import TheSidebar from '@/components/TheSidebar.vue';

</script>

<style lang="scss">
.app {
  display: flex;

  .col-2 {
    margin: 2.25rem 0;
    margin-left: 2rem;
  }
}

</style>
