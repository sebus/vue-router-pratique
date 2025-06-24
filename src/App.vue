<script setup>
import { RouterView, RouterLink } from 'vue-router'
</script>

<template>
  <header>
    <nav>
      <RouterLink :to="{ name: 'home' }">Home</RouterLink>
      <RouterLink :to="{ name: 'users' }">Users</RouterLink>
    </nav>
  </header>

  <RouterView />
</template>

<style scoped>
nav {
  display: flex;
  flex-direction: row;
  gap: 28px;

  a {
    color: black;
  }
}
</style>
