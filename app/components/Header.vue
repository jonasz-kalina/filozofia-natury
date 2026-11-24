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
        <NuxtLink to="/" class="logo">Filozofia Natury</NuxtLink>
      </div>
      <div class="nav-right">
        <a href="#" class="social"><i class="pi pi-twitter"></i></a>
        <a href="#" class="social"><i class="pi pi-facebook"></i></a>
        <a href="#" class="social"><i class="pi pi-tiktok"></i></a>
      </div>
    </nav>
  </header>
</template>

<style scoped>
.header {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 100;
  padding: 20px 40px;
  background: #2f4243a6;
  max-height: 100px;
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
</style>