<template>
  <section class="about-space">
    <div class="container">
      <div class="space-grid">
        <div class="card">
          <img src="/images/about-namioty.jpg" alt="Namioty" />
          <h4>Namioty</h4>
          <p>Kilka kopuł glampingowych z ciepłym światłem wewnątrz.</p>
        </div>
        <div class="card">
          <img src="/images/about-ogien.jpg" alt="Ognisko" />
          <h4>Ognisko</h4>
          <p>Wieczory przy ogniu — rozmowy albo cisza.</p>
        </div>
        <div class="card">
          <img src="/images/about-stol.jpg" alt="Stół" />
          <h4>Stół na zewnątrz</h4>
          <p>Śniadania i kolacje pod drzewami.</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-space {
  padding: 80px 0;
  background: #1d382e;
}
.container {
  max-width: 1100px;
  margin: 0 auto;
  padding: 0 24px;
}
.space-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
}
.card img {
  width: 100%;
  height: auto;
  aspect-ratio: 2 / 3;
  object-fit: cover;
  border-radius: 12px;
  margin-bottom: 16px;
}
.card h4 {
  font-size: 1.2rem;
  margin-bottom: 8px;
  color: #f0f5f2;
}
.card p {
  font-size: 0.95rem;
  color: #b8d0c4;
  line-height: 1.5;
}
@media (max-width: 768px) {
  .space-grid { grid-template-columns: 1fr; }
  .about-space { padding: 60px 0; }
}
</style>