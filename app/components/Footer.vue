<template>
  <footer class="footer">
    <div class="footer-top">
      <div class="footer-cta">
        <h2>Got an idea?</h2>
        <p class="cta-accent">Let's talk.</p>
      </div>
      <div class="footer-contact">
        <a href="mailto:hello@filozofianatury.pl" class="contact-email">hello@filozofianatury.pl</a>
        <a href="tel:+48123456789" class="contact-phone">+48 123 456 789</a>
        <NuxtLink to="/contact" class="contact-btn">
          Start a project
          <span class="btn-arrow">→</span>
        </NuxtLink>
      </div>
    </div>

    <div class="footer-divider"></div>

    <div class="footer-columns">
      <div class="footer-col">
        <h4>SITEMAP</h4>
        <NuxtLink to="/">Home</NuxtLink>
        <NuxtLink to="/about">About</NuxtLink>
        <NuxtLink to="/services">Services</NuxtLink>
        <NuxtLink to="/blog">Blog</NuxtLink>
        <NuxtLink to="/contact">Contact</NuxtLink>
      </div>
      <div class="footer-col">
        <h4>SOCIALS</h4>
        <a href="#" target="_blank">Instagram <span>↗</span></a>
        <a href="#" target="_blank">Facebook <span>↗</span></a>
        <a href="#" target="_blank">TikTok <span>↗</span></a>
        <a href="#" target="_blank">LinkedIn <span>↗</span></a>
      </div>
      <div class="footer-col">
        <h4>STUDIO</h4>
        <p>ul. Przykładowa 12</p>
        <p>00-001 Warszawa</p>
        <p>Polska</p>
        <a href="#" class="directions">Get directions <span>→</span></a>
      </div>
      <div class="footer-col">
        <h4>LOCAL TIME</h4>
        <div class="local-time">{{ currentTime }}</div>
        <p class="time-note">● Studio open · we reply by 18:00</p>
      </div>
    </div>

    <div class="footer-logo">
      <span>Filozofia Natury</span>
    </div>

    <div class="footer-bottom">
      <span>© {{ year }} Filozofia Natury. All rights reserved.</span>
      <div class="footer-links">
        <NuxtLink to="/privacy">Privacy</NuxtLink>
        <NuxtLink to="/terms">Terms</NuxtLink>
        <NuxtLink to="/cookies">Cookies</NuxtLink>
      </div>
    </div>
  </footer>
</template>

<script setup>
const year = new Date().getFullYear()
const currentTime = ref('')

function updateTime() {
  const now = new Date()
  currentTime.value = now.toLocaleTimeString('pl-PL', { hour: '2-digit', minute: '2-digit', second: '2-digit' })
}

onMounted(() => {
  updateTime()
  setInterval(updateTime, 1000)
})
</script>

<style scoped>
.footer {
  background: #1a2420;
  color: #b8c8bc;
  padding: 80px 60px 30px;
  position: relative;
  overflow: hidden;
}

.footer-top {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 50px;
}

.footer-cta h2 {
  font-size: 3.5rem;
  font-weight: 500;
  color: #f0f5f2;
  margin: 0;
  line-height: 1;
}

.cta-accent {
  font-size: 3.5rem;
  font-style: italic;
  color: #e85a2a;
  margin: 0;
  line-height: 1;
}

.footer-contact {
  text-align: right;
}

.contact-email {
  display: block;
  font-size: 1.8rem;
  color: #f0f5f2;
  text-decoration: none;
  margin-bottom: 8px;
}

.contact-phone {
  display: block;
  font-size: 0.95rem;
  color: #7a9a8a;
  text-decoration: none;
  margin-bottom: 20px;
}

.contact-btn {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  background: #e85a2a;
  color: #fff;
  padding: 14px 24px;
  border-radius: 30px;
  text-decoration: none;
  font-size: 0.9rem;
  font-weight: 500;
}

.btn-arrow {
  width: 28px;
  height: 28px;
  background: #fff;
  color: #e85a2a;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.8rem;
}

.footer-divider {
  height: 1px;
  background: #2a3a32;
  margin: 30px 0;
  position: relative;
}

.footer-divider::before {
  content: '';
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  width: 12px;
  height: 12px;
  border: 1px solid #3a4a42;
  border-radius: 50%;
  background: #1a2420;
}

.footer-divider::after {
  content: '';
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  width: 4px;
  height: 4px;
  background: #e85a2a;
  border-radius: 50%;
}

.footer-columns {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 40px;
  margin-bottom: 60px;
}

.footer-col h4 {
  font-size: 0.65rem;
  letter-spacing: 2px;
  color: #6a8a7a;
  margin: 0 0 20px;
  font-weight: 500;
}

.footer-col a,
.footer-col p {
  display: block;
  color: #9ab0a4;
  text-decoration: none;
  font-size: 0.95rem;
  margin-bottom: 10px;
  transition: color 0.2s;
}

.footer-col a:hover {
  color: #f0f5f2;
}

.footer-col a span {
  font-size: 0.75rem;
  margin-left: 4px;
}

.directions {
  margin-top: 10px;
}

.local-time {
  font-size: 2.5rem;
  font-weight: 500;
  color: #e85a2a;
  letter-spacing: 2px;
  margin-bottom: 10px;
}

.time-note {
  font-size: 0.8rem;
  color: #6a8a7a;
}

.footer-logo {
  text-align: center;
  margin: 40px 0 50px;
}

.footer-logo span {
  font-size: 12rem;
  font-weight: 600;
  color: transparent;
  background: linear-gradient(180deg, #e85a2a 0%, #c44a1a 100%);
  -webkit-background-clip: text;
  background-clip: text;
  line-height: 0.85;
  letter-spacing: -4px;
}

.footer-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: 20px;
  border-top: 1px solid #2a3a32;
  font-size: 0.8rem;
  color: #5a6a62;
}

.footer-links {
  display: flex;
  gap: 24px;
}

.footer-links a {
  color: #5a6a62;
  text-decoration: none;
}

.footer-links a:hover {
  color: #9ab0a4;
}

@media (max-width: 900px) {
  .footer { padding: 50px 24px 20px; }
  .footer-top { flex-direction: column; gap: 30px; }
  .footer-cta h2, .cta-accent { font-size: 2.4rem; }
  .footer-contact { text-align: left; }
  .contact-email { font-size: 1.3rem; }
  .footer-columns { grid-template-columns: repeat(2, 1fr); gap: 30px; }
  .footer-logo span { font-size: 4rem; }
  .footer-bottom { flex-direction: column; gap: 12px; text-align: center; }
}
</style>