<template>
  <section class="about-philosophy">
    <div class="container">
      <div class="philosophy-grid">
        <div class="item">
          <h3>Cisza</h3>
          <p>Tu nie ma programu. Możesz spacerować, czytać, siedzieć przy ogniu albo nic nie robić.</p>
        </div>
        <div class="item">
          <h3>Prostota</h3>
          <p>Domek holenderski z dużymi oknami, kilka namiotów glampingowych, stół na zewnątrz. Nic więcej nie trzeba.</p>
        </div>
        <div class="item">
          <h3>Obecność</h3>
          <p>Nie jesteśmy retreatem. Jesteśmy miejscem, w którym możesz być ze sobą i z innymi kobietami bez presji.</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-philosophy {
  padding: 80px 0;
  background: #162e25;
}
.container {
  max-width: 1100px;
  margin: 0 auto;
  padding: 0 24px;
}
.philosophy-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 40px;
}
.item h3 {
  font-size: 1.5rem;
  font-weight: 500;
  margin-bottom: 12px;
  color: #e85a2a;
}
.item p {
  font-size: 1rem;
  line-height: 1.6;
  color: #b8d0c4;
}
@media (max-width: 768px) {
  .philosophy-grid { grid-template-columns: 1fr; gap: 32px; }
  .about-philosophy { padding: 60px 0; }
}
</style>