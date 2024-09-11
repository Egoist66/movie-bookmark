<script setup lang="ts">
import {RouterView } from 'vue-router'
import Header from '@/components/partials/Header.vue'
</script>

<template>

  <Header />

  <main class="py-5">

    <div class="container m-auto">

      <RouterView/>

    </div>

    
  </main>
</template>

<style scoped>
  main {
    min-height: 100vh;
  }

</style>
