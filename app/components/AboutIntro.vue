<template>
  <section class="about-intro">
    <div class="container">
      <div class="intro-grid">
        <div class="intro-text">
          <span class="label">O NAS</span>
          <h1>Tu <span>zwalniasz</span></h1>
          <p class="lead">
            Jesteśmy małym miejscem w lesie, stworzonym dla kobiet, które chcą na chwilę odłożyć wszystko inne.
          </p>
          <p>
            Nie organizujemy warsztatów rozwoju osobistego. Nie uczymy medytacji. 
            Po prostu dajemy przestrzeń — domek z dużymi oknami, kilka namiotów, ognisko i ciszę, której w codzienności coraz mniej.
          </p>
          <p>
            Przyjeżdżasz na weekend. Zostajesz na tyle, na ile chcesz.
          </p>
        </div>
        <div class="intro-image">
          <img src="/images/about-domek.jpg" alt="Domek w lesie" />
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-intro {
  padding: 120px 0 80px;
  background: #1d382e;
  color: #e8f0ea;
}
.container {
  max-width: 1100px;
  margin: 0 auto;
  padding: 0 24px;
}
.intro-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
}
.label {
  font-size: 0.75rem;
  letter-spacing: 2px;
  color: #7a9a8a;
  text-transform: uppercase;
  display: block;
  margin-bottom: 16px;
}
h1 {
  font-size: 3.8rem;
  font-weight: 500;
  line-height: 0.95;
  margin: 0 0 28px;
  color: #f0f5f2;
}
h1 span {
  font-style: italic;
  color: #e85a2a;
}
.lead {
  font-size: 1.4rem;
  line-height: 1.45;
  margin-bottom: 20px;
  color: #f0f5f2;
}
p {
  font-size: 1.05rem;
  line-height: 1.7;
  color: #b8d0c4;
  margin-bottom: 16px;
}
.intro-image img {
  width: 100%;
  height: 420px;
  object-fit: cover;
  border-radius: 12px;
}
@media (max-width: 768px) {
  .intro-grid { grid-template-columns: 1fr; gap: 40px; }
  .about-intro { padding: 90px 0 60px; }
  h1 { font-size: 2.8rem; }
  .intro-image img { height: 280px; }
}
</style>