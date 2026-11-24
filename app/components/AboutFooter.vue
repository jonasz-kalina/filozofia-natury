<template>
  <footer class="about-footer">
    <div class="footer-inner">
      <div class="footer-left">
        <span class="footer-label">2027</span>
        <h2>Zostań <span>na dłużej</span></h2>
        <p>Jeśli czujesz, że to miejsce jest dla Ciebie — napisz.</p>
      </div>

      <div class="footer-logo">
        <svg viewBox="0 0 220 100" class="logo-trees">
          <defs>
            <linearGradient id="grad" x1="0%" y1="0%" x2="0%" y2="100%">
              <stop offset="0%" style="stop-color:#e85a2a" />
              <stop offset="100%" style="stop-color:#c44a1a" />
            </linearGradient>
          </defs>
          <!-- kamyczki lewa -->
          <ellipse cx="18" cy="92" rx="10" ry="5" fill="#3a4a42"/>
          <ellipse cx="32" cy="94" rx="6" ry="3" fill="#2a3a32"/>
          <!-- białe drzewko (z tyłu) -->
          <path d="M120 35 L110 52 L116 52 L108 66 L114 66 L106 78 H134 L126 66 L132 66 L124 52 L130 52 Z" fill="#f0f5f2" opacity="0.9"/>
          <rect x="116" y="78" width="6" height="7" fill="#f0f5f2" opacity="0.9"/>
          <!-- małe pomarańczowe -->
          <path d="M50 40 L40 58 L46 58 L38 74 L44 74 L36 88 H64 L56 74 L62 74 L54 58 L60 58 Z" fill="url(#grad)" opacity="0.75"/>
          <rect x="46" y="88" width="6" height="8" fill="#e85a2a" opacity="0.75"/>
          <!-- średnie pomarańczowe -->
          <path d="M100 18 L77 50 L87 50 L71 72 L83 72 L67 90 H133 L117 72 L129 72 L113 50 L123 50 Z" fill="url(#grad)"/>
          <rect x="93" y="90" width="14" height="8" fill="#e85a2a"/>
          <!-- małe pomarańczowe -->
          <path d="M165 42 L155 58 L161 58 L153 72 L159 72 L151 86 H179 L171 72 L177 72 L169 58 L175 58 Z" fill="url(#grad)" opacity="0.65"/>
          <rect x="161" y="86" width="6" height="7" fill="#e85a2a" opacity="0.65"/>
          <!-- kamyczki prawa -->
          <ellipse cx="190" cy="93" rx="8" ry="4" fill="#3a4a42"/>
          <ellipse cx="202" cy="95" rx="5" ry="2.5" fill="#2a3a32"/>
        </svg>
      </div>

      <div class="footer-right">
        <a href="mailto:hello@filozofianatury.pl" class="footer-email">
          hello@filozofianatury.pl
        </a>
        <NuxtLink to="/contact" class="footer-btn">
          Napisz do nas
          <span>→</span>
        </NuxtLink>
      </div>
    </div>

    <div class="footer-bottom">
      <span>© {{ year }} Filozofia Natury</span>
      <div class="footer-links">
        <NuxtLink to="/">Home</NuxtLink>
        <NuxtLink to="/services">Services</NuxtLink>
        <NuxtLink to="/blog">Blog</NuxtLink>
      </div>
    </div>
  </footer>
</template>

<script setup>
const year = new Date().getFullYear()
</script>

<style scoped>
.about-footer {
  background: #0f1c18;
  color: #b8d0c4;
  padding: 100px 60px 40px;
  position: relative;
}

.footer-inner {
  display: grid;
  grid-template-columns: 1fr 240px 1fr;
  align-items: flex-end;
  gap: 40px;
  margin-bottom: 80px;
}

.footer-label {
  font-size: 0.75rem;
  letter-spacing: 2px;
  color: #6a8a7a;
  display: block;
  margin-bottom: 12px;
}

.footer-left h2 {
  font-size: 4rem;
  font-weight: 500;
  color: #f0f5f2;
  margin: 0 0 16px;
  line-height: 0.9;
}

.footer-left h2 span {
  font-style: italic;
  color: #e85a2a;
}

.footer-left p {
  font-size: 1.05rem;
  color: #8aaa9a;
  margin: 0;
  max-width: 320px;
}

.footer-logo {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.logo-trees {
  width: 220px;
  height: 120px;
}

.footer-right {
  text-align: right;
}

.footer-email {
  display: block;
  font-size: 1.4rem;
  color: #f0f5f2;
  text-decoration: none;
  margin-bottom: 20px;
}

.footer-btn {
  display: inline-flex;
  align-items: center;
  gap: 12px;
  background: transparent;
  border: 1px solid #e85a2a;
  color: #e85a2a;
  padding: 14px 28px;
  border-radius: 30px;
  text-decoration: none;
  font-size: 0.95rem;
  transition: all 0.3s;
}

.footer-btn:hover {
  background: #e85a2a;
  color: #fff;
}

.footer-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: 30px;
  border-top: 1px solid #1e2e28;
  font-size: 0.85rem;
  color: #5a6a62;
}

.footer-links {
  display: flex;
  gap: 28px;
}

.footer-links a {
  color: #6a8a7a;
  text-decoration: none;
}

.footer-links a:hover {
  color: #f0f5f2;
}

@media (max-width: 900px) {
  .about-footer { padding: 60px 24px 30px; }
  .footer-inner { 
    grid-template-columns: 1fr; 
    gap: 40px; 
  }
  .footer-left h2 { font-size: 2.6rem; }
  .logo-trees { width: 180px; height: 100px; }
  .footer-right { text-align: left; }
  .footer-email { font-size: 1.2rem; }
  .footer-bottom { flex-direction: column; gap: 16px; text-align: center; }
}
</style>