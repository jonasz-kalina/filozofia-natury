<template>
  <header class="header">
    <nav class="nav">
      <div class="nav-left">
        <NuxtLink to="/">Home</NuxtLink>
        <NuxtLink to="/about">About</NuxtLink>
        <NuxtLink to="/services">Services</NuxtLink>
        <NuxtLink to="/blog">Blog</NuxtLink>
        <NuxtLink to="/contact">Contact</NuxtLink>
      </div>

      <div class="nav-center">
        <NuxtLink to="/" class="logo">
          Filozofia Natury
        </NuxtLink>
      </div>

      <div class="nav-right">
        <a href="#" class="social"><i class="pi pi-twitter"></i></a>
        <a href="#" class="social"><i class="pi pi-facebook"></i></a>
        <a href="#" class="social"><i class="pi pi-tiktok"></i></a>
      </div>

      <button
        class="mobile-toggle"
        @click="menuOpen = !menuOpen"
      >
        <i
          :class="menuOpen ? 'pi pi-times' : 'pi pi-bars'"
        ></i>
      </button>
    </nav>

    <transition name="mobile-menu">
      <div
        v-if="menuOpen"
        class="mobile-menu"
      >
        <NuxtLink to="/" @click="menuOpen = false">Home</NuxtLink>
        <NuxtLink to="/about" @click="menuOpen = false">About</NuxtLink>
        <NuxtLink to="/services" @click="menuOpen = false">Services</NuxtLink>
        <NuxtLink to="/blog" @click="menuOpen = false">Blog</NuxtLink>
        <NuxtLink to="/contact" @click="menuOpen = false">Contact</NuxtLink>
      </div>
    </transition>
  </header>
</template>

<script setup>
import { ref } from 'vue'

const menuOpen = ref(false)
</script>

<style scoped>
.header {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 100;
  padding: 20px 40px;
  background: #2f4243a6;
}

.nav {
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  align-items: center;
  color: white;
  font-weight: 400;
}

.nav-left {
  justify-self: start;
}

.nav-center {
  justify-self: center;
}

.nav-right {
  justify-self: end;
}

.nav a {
  color: inherit;
  text-decoration: none;
  margin: 0 15px;
  display: inline-block;
  text-align: center;
  position: relative;
  padding-bottom: 2px;
}

.nav-left a.router-link-active::after,
.nav-left a.router-link-exact-active::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -2px;
  width: 100%;
  height: 2px;
  background: #e85a2a;
}

.logo {
  font-size: 1.4rem;
  font-weight: 600;
  margin: 0;
}

.mobile-toggle {
  display: none;

  background: transparent;
  border: none;
  color: white;

  font-size: 1.6rem;
  cursor: pointer;
}

/* 1100 */

@media (max-width: 1100px) {
  .header {
    padding: 16px 24px;
  }

  .nav a {
    margin: 0 10px;
    font-size: 0.95rem;
  }

  .logo {
    font-size: 1.25rem;
  }
}

/* 900 */

@media (max-width: 900px) {
  .header {
    padding: 12px 18px;
  }

  .nav a {
    margin: 0 7px;
    font-size: 0.9rem;
  }

  .logo {
    font-size: 1.05rem;
  }
}

/* MOBILE */

@media (max-width: 700px) {
  .nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .nav-left,
  .nav-right {
    display: none;
  }

  .mobile-toggle {
    display: block;
  }

  .logo {
    font-size: 1.1rem;
  }

  .mobile-menu {
    position: absolute;
    top: 100%;
    left: 0;

    width: 100%;

    background: rgba(20, 30, 30, 0.97);

    display: flex;
    flex-direction: column;
    align-items: center;

    padding: 20px;
  }

  .mobile-menu a {
    color: white;
    text-decoration: none;

    width: 100%;
    text-align: center;

    padding: 12px 0;

    font-size: 1rem;
  }
}
</style>