<template>
  <section class="services">
    <div class="services-header">
      <span class="label">Co tu robimy</span>
      <h1>Warsztaty i czas dla siebie</h1>
      <p>Namioty to tylko miejsce na noc. Reszta to las, jezioro i spotkania w małej grupie.</p>
    </div>

    <div class="services-list">
      <div class="service-item">
        <div class="service-image" data-parallax>
          <img src="/images/services-terapia.jpg" alt="Terapia leśna" />
          <span class="big-number">01</span>
        </div>
        <div class="service-content">
          <span class="service-tag">Terapia leśna</span>
          <h2>Spacer bez celu</h2>
          <p>Idziemy wolno. Patrzymy, słuchamy, zbieramy to, co leży pod nogami. Bez przewodnika, który mówi co masz czuć. Czasem po prostu stoimy i słuchamy lasu. Czasem siadamy na mchu i milczymy. Nie ma harmonogramu, nie ma punktów do odhaczenia. Tylko ty, ścieżka i to, co akurat jest wokół.</p>
          <NuxtLink to="/contact" class="link">Zapytaj →</NuxtLink>
        </div>
      </div>

      <div class="service-item reverse">
        <div class="service-image" data-parallax>
          <img src="/images/services-grzyby.jpg" alt="Grzyby" />
          <span class="big-number">02</span>
        </div>
        <div class="service-content">
          <span class="service-tag">Grzyby</span>
          <h2>To, co rośnie dookoła</h2>
          <p>Pokazujemy, co można zebrać, co z tego zrobić, jak to pachnie. Nic na siłę. Tylko to, co chcesz zabrać ze sobą. Borowiki, podgrzybki, kurki — uczymy się je rozpoznawać i zbierać spokojnie, bez pośpiechu. Potem można ususzyć, zrobić sos albo po prostu zostawić w lesie. Ty decydujesz.</p>
          <NuxtLink to="/contact" class="link">Zapytaj →</NuxtLink>
        </div>
      </div>

      <div class="service-item">
        <div class="service-image" data-parallax>
          <img src="/images/services-jezioro.jpg" alt="Jezioro" />
          <span class="big-number">03</span>
        </div>
        <div class="service-content">
          <span class="service-tag">Jezioro</span>
          <h2>Woda i cisza</h2>
          <p>Rano albo wieczorem. Można pływać, siedzieć na brzegu albo tylko patrzeć. Jezioro jest tuż obok. Mgła nad wodą, kajak na brzegu, cisza która nie przeszkadza. Nie trzeba nic robić — woda sama ustawia tempo. Można usiąść na pomoście z kubkiem herbaty i po prostu być.</p>
          <NuxtLink to="/contact" class="link">Zapytaj →</NuxtLink>
        </div>
      </div>

      <div class="service-item reverse">
        <div class="service-image" data-parallax>
          <img src="/images/services-kobiety.jpg" alt="Spotkania" />
          <span class="big-number">04</span>
        </div>
        <div class="service-content">
          <span class="service-tag">Spotkania</span>
          <h2>Mała grupa kobiet</h2>
          <p>Wieczór przy ognisku. Rozmowa albo cisza. Bez planu, który trzeba wypełnić. Tylko ty i inne, które też tu przyjechały odpocząć. Koc, ogień, ciepły napój. Czasem ktoś coś powie, czasem nikt nic nie mówi. Obie rzeczy są w porządku. Nie ma oczekiwań, nie ma ról do odegrania.</p>
          <NuxtLink to="/contact" class="link">Zapytaj →</NuxtLink>
        </div>
      </div>
    </div>

    <div class="services-cta">
      <NuxtLink to="/contact" class="cta-btn">
        Zapytaj o terminy
        <span>→</span>
      </NuxtLink>
    </div>
  </section>
</template>

<script setup>
onMounted(() => {
  const images = document.querySelectorAll('[data-parallax] img')
  
  const handleScroll = () => {
    images.forEach((img) => {
      const rect = img.parentElement.getBoundingClientRect()
      const speed = 0.25
      const offset = (rect.top - window.innerHeight / 2) * speed
      img.style.transform = `translateY(${offset}px)`
    })
  }

  window.addEventListener('scroll', handleScroll, { passive: true })
  handleScroll()
})
</script>

<style scoped>
.services {
  background: #0f1c18;
  color: #b8d0c4;
  padding: 100px 60px;
}

.services-header {
  max-width: 680px;
  margin-bottom: 70px;
}

.label {
  font-size: 0.75rem;
  letter-spacing: 2px;
  color: #6a8a7a;
  display: block;
  margin-bottom: 16px;
}

.services-header h1 {
  font-size: 3.6rem;
  font-weight: 500;
  color: #f0f5f2;
  margin: 0 0 16px;
  line-height: 1;
}

.services-header p {
  font-size: 1.15rem;
  color: #8aaa9a;
  margin: 0;
  line-height: 1.5;
}

.services-list {
  display: flex;
  flex-direction: column;
  gap: 60px;
  margin-bottom: 80px;
}

.service-item {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  align-items: center;
}

.service-item.reverse {
  direction: rtl;
}

.service-item.reverse .service-content {
  direction: ltr;
}

.service-image {
  position: relative;
  overflow: hidden;
  border-radius: 16px;
  height: 360px;
}

.service-image img {
  width: 100%;
  height: 130%;
  object-fit: cover;
  position: absolute;
  top: -15%;
  left: 0;
  transition: transform 0.1s linear;
}

.big-number {
  position: absolute;
  top: 20px;
  right: 20px;
  font-size: 7rem;
  font-weight: 600;
  color: #e85a2a;
  line-height: 0.8;
  opacity: 0.9;
  pointer-events: none;
  z-index: 2;
}

.service-tag {
  font-size: 0.75rem;
  letter-spacing: 1px;
  color: #e85a2a;
  display: block;
  margin-bottom: 10px;
}

.service-content h2 {
  font-size: 2.2rem;
  font-weight: 500;
  color: #f0f5f2;
  margin: 0 0 12px;
  line-height: 1.1;
}

.service-content p {
  font-size: 1.05rem;
  color: #8aaa9a;
  margin: 0 0 16px;
  line-height: 1.6;
  max-width: 420px;
}

.link {
  color: #e85a2a;
  text-decoration: none;
  font-size: 0.95rem;
  font-weight: 500;
}

.link:hover {
  text-decoration: underline;
}

.services-cta {
  text-align: center;
}

.cta-btn {
  display: inline-flex;
  align-items: center;
  gap: 12px;
  background: transparent;
  border: 1px solid #e85a2a;
  color: #e85a2a;
  padding: 16px 36px;
  border-radius: 30px;
  text-decoration: none;
  font-size: 1rem;
  transition: all 0.3s;
}

.cta-btn:hover {
  background: #e85a2a;
  color: #fff;
}

@media (max-width: 900px) {
  .services { padding: 80px 24px; }
  .services-header h1 { font-size: 2.6rem; }
  .service-item, .service-item.reverse {
    grid-template-columns: 1fr;
    direction: ltr;
    gap: 20px;
  }
  .service-image { height: 260px; }
  .big-number { font-size: 5rem; top: 12px; right: 12px; }
  .service-content h2 { font-size: 1.8rem; }
}
</style>