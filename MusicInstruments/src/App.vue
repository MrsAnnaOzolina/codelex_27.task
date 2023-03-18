<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/PaintingWall.vue'
</script>

<template>
  <header>
    <div class="header">
      <nav>
        <RouterLink class="header__link" to="/">Home</RouterLink>
        <RouterLink  class="header__link" to="/about">About</RouterLink>
      </nav>
</div>
  </header>

  <RouterView />
</template>

<style scoped>
.header{
  display: flex;
  justify-content: center;
}
.header__link{
  font-family: 'Beth Ellen', cursive;
font-family: 'Shadows Into Light', cursive;
  color: rgb(66, 62, 62);
  margin: 30px;
  font-size: 1.2em;
}
</style>
