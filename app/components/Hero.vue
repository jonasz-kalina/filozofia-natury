<template>
  <section class="hero">
    <div class="hero-overlay"></div>
    <div class="hero-content">
      <h1>Filozofia Natury</h1>
      <p>Teraz nadszedł Twój czas...</p>
    </div>
    <svg class="skew" viewBox="0 0 1440 100" preserveAspectRatio="none">
      <path d="M0,0 L480,100 L1440,0 L1440,100 L0,100 Z" fill="#dde4d7"/>
    </svg>
  </section>
</template>

<style scoped>
.hero {
  height: 100vh;
  background-image: url('/images/hero-bg.jpg');
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  text-align: center;
  position: relative;
  overflow: hidden;
}

.hero-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to bottom,
    rgba(0, 0, 0, 0.35) 0%,
    rgba(0, 0, 0, 0.35) 60%,
    rgba(15, 28, 24, 0.6) 85%,
    #0f1c18 100%
  );
  z-index: 1;
}

.hero-content {
  position: relative;
  z-index: 2;
  padding: 0 20px;
}

.hero-content h1 {
  font-size: 9rem;
  font-weight: 400;
  margin: 0;
}

.hero-content p {
  font-size: 1.2rem;
  margin-top: 10px;
  opacity: 0.8;
}

.skew {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 140px;
  z-index: 2;
}

/* MOBILE */

@media (max-width: 700px) {
  .hero-content h1 {
    font-size: 6rem;
    line-height: 0.95;
  }

  .hero-content p {
    font-size: 1rem;
    margin-top: 20px;
  }

  .skew {
    height: 100px;
  }
}

/* SMALL MOBILE */

@media (max-width: 380px) {
  .hero-content {
    padding: 0 16px;
  }

  .hero-content h1 {
    font-size: 4.8rem;
    line-height: 0.92;
  }

  .hero-content p {
    font-size: 0.95rem;
    margin-top: 16px;
  }

  .skew {
    height: 80px;
  }
}
</style>