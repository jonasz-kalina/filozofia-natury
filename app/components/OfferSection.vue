<template>
  <section class="offer">
    <h2>What I have to <span>offer</span> you</h2>

    <div class="cards">
      <!-- Personal Growth -->
      <div class="card">
        <div class="card-image">
          <img src="/images/personal-growth.jpg" alt="Personal Growth" />
          <div class="card-overlay">
            <h3>Personal Growth</h3>
            <div class="accordion">
              <details>
                <summary>About</summary>
                <p>Short description about personal growth sessions.</p>
              </details>
              <details>
                <summary>Pricing</summary>
                <p>Session pricing details.</p>
              </details>
            </div>
            <button class="btn">Book An Appointment</button>
          </div>
        </div>
      </div>

      <!-- Forest Therapy -->
      <div class="card">
        <div class="card-image">
          <img src="/images/forest-therapy.jpg" alt="Forest Therapy" />
          <div class="card-overlay">
            <h3>Forest Therapy</h3>
            <div class="accordion">
              <details>
                <summary>About</summary>
                <p>Short description about forest therapy.</p>
              </details>
              <details>
                <summary>Pricing</summary>
                <p>Session pricing details.</p>
              </details>
            </div>
            <button class="btn">Book An Appointment</button>
          </div>
        </div>
      </div>

      <!-- Wisdom Walks -->
      <div class="card">
        <div class="card-image">
          <img src="/images/wisdom-walks.jpg" alt="Wisdom Walks" />
          <div class="card-overlay">
            <h3>Wisdom Walks</h3>
            <div class="accordion">
              <details>
                <summary>About</summary>
                <p>Short description about wisdom walks.</p>
              </details>
              <details>
                <summary>Pricing</summary>
                <p>Session pricing details.</p>
              </details>
            </div>
            <button class="btn">Book An Appointment</button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.offer {
  background: #1d382e;
  padding: 100px 40px 140px;
  text-align: center;
  position: relative;
  border-radius: 0 0 60px 60px;
  margin-bottom: -80px;
  z-index: 2;
}

.offer h2 {
  color: #dde4d7;
  font-size: 3.2rem;
  font-weight: 500;
  margin: 0 0 60px;
}

.offer h2 span {
  font-style: italic;
  color: #e85a2a;
}

.cards {
  display: flex;
  gap: 28px;
  justify-content: center;
  max-width: 1200px;
  margin: 0 auto;
}

.card {
  flex: 1;
  max-width: 340px;
  border-radius: 24px;
  overflow: hidden;
  background: #0f241c;
  position: relative;
  min-height: 480px;
}

.card-image {
  position: relative;
  height: 100%;
  overflow: hidden;
}

.card-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 1.2s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

.card:hover .card-image img {
  transform: scale(1.06);
}

.card-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to bottom, rgba(0,0,0,0.12) 0%, rgba(0,0,0,0.4) 50%, rgba(0,0,0,0.72) 100%);
  padding: 28px 22px 24px;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  color: #dde4d7;
  text-align: left;
  transition: background 0.9s ease;
}

.card:hover .card-overlay {
  background: linear-gradient(to bottom, rgba(0,0,0,0.18) 0%, rgba(0,0,0,0.48) 50%, rgba(0,0,0,0.78) 100%);
}

.card-overlay h3 {
  font-size: 1.6rem;
  font-weight: 500;
  margin: 0 0 18px;
  color: #dde4d7;
}

.accordion details {
  border-bottom: 1px solid rgba(221, 228, 215, 0.25);
  margin-bottom: 4px;
}

.accordion summary {
  padding: 10px 0;
  cursor: pointer;
  list-style: none;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 0.95rem;
}

.accordion summary::-webkit-details-marker {
  display: none;
}

.accordion summary::after {
  content: "▾";
  font-size: 0.8rem;
  opacity: 0.7;
}

.accordion details[open] summary::after {
  content: "▴";
}

.accordion p {
  font-size: 0.88rem;
  line-height: 1.5;
  margin: 6px 0 12px;
  opacity: 0.85;
}

.btn {
  margin-top: 18px;
  padding: 12px 28px;
  background: #e85a2a;
  color: #fff;
  border: none;
  border-radius: 30px;
  cursor: pointer;
  font-size: 0.95rem;
  align-self: flex-start;
  transition: background 0.3s ease;
}

.btn:hover {
  background: #f06a3a;
}

@media (max-width: 900px) {
  .cards {
    flex-direction: column;
    align-items: center;
  }
  .card {
    width: 100%;
    max-width: 420px;
  }
}
</style>