<script setup>
import { ref, computed } from 'vue'
import Home from './pages/home/index.vue'
import Auth from './pages/auth/index.vue'
import Register from './pages/register/index.vue'

const routes = {
  '': Home,
  'auth': Auth,
  'register': Register,
}

const currentPath = ref(window.location.hash)

window.addEventListener('hashchange', () => {
  currentPath.value = window.location.hash
})

const currentView = computed(() => {
  return routes[currentPath.value.slice(1) || '']
})
</script>

<template>
  <a href="#">Home</a> |
  <a href="#auth">Auth</a> |
  <a href="#register">Register</a> |
  <component :is="currentView" />
</template>