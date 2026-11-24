<template>
  <section class="about-closing">
    <div class="container">
      <p>
        Jeśli szukasz miejsca, w którym nikt od Ciebie nic nie chce — jesteś we właściwym miejscu.
      </p>
    </div>
  </section>
</template>

<style scoped>
.about-closing {
  padding: 100px 0;
  background: #162e25;
  text-align: center;
}
.container {
  max-width: 700px;
  margin: 0 auto;
  padding: 0 24px;
}
p {
  font-size: 1.6rem;
  line-height: 1.5;
  color: #f0f5f2;
  font-style: italic;
}
@media (max-width: 768px) {
  .about-closing { padding: 70px 0; }
  p { font-size: 1.3rem; }
}
</style>