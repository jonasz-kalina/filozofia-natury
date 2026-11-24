<template>
  <section class="content-image right">
    <div class="content-box">
      <span class="label">Blog</span>
      <h2>A day in the life</h2>
      <p>
        Greetings, cherished seekers of growth and wisdom! Today, I invite you to step into a day in my life, where the whispering trees and rustling leaves are my trusted companions on this journey of empowerment.
      </p>
      <p>
        As the sun gently paints the sky with hues of dawn, my day begins with a silent communion with nature. A forest walk, where every step is a dance with the earth, sets the tone for what lies ahead. The tranquil surroundings become my morning canvas, inspiring the day's purpose.
      </p>
      <button class="btn">Read more</button>
    </div>

    <div class="image-box">
      <img src="/images/blog-day.jpg" alt="A day in the life" />
    </div>
  </section>
</template>

<style scoped>
.content-image {
  display: flex;
  align-items: center;
  gap: 28px;
  background: #1d382e;
  padding: 70px 0 70px 0;
  overflow: hidden;
}

.content-image.right {
  flex-direction: row-reverse;
  padding: 70px 0 70px 0;
}

.content-box {
  flex: 0 0 34%;
  background: #dde4d7;
  color: #1d382e;
  padding: 50px 40px;
  border-radius: 30px;
  margin-right: 30px;
}

.label {
  display: block;
  font-size: 0.85rem;
  letter-spacing: 0.06em;
  color: #e85a2a;
  font-weight: 500;
  margin-bottom: 10px;
}

.content-box h2 {
  font-size: 2.6rem;
  font-weight: 500;
  line-height: 1.1;
  margin: 0 0 22px;
}

.content-box p {
  font-size: 0.98rem;
  line-height: 1.65;
  margin: 0 0 16px;
  opacity: 0.9;
  max-width: 420px;
}

.btn {
  margin-top: 10px;
  padding: 13px 32px;
  background: #e85a2a;
  color: #fff;
  border: none;
  border-radius: 40px;
  cursor: pointer;
  font-size: 0.95rem;
  transition: background 0.3s ease;
}

.btn:hover {
  background: #f06a3a;
}

.image-box {
  flex: 0 0 63%;
  aspect-ratio: 1.8 / 1;
  overflow: hidden;
  border-radius: 0 42px 42px 0;
}

.image-box img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center 30%;
  transition: transform 0.8s ease;
}

.image-box:hover img {
  transform: scale(1.08);
}

/* 1250 */

@media (max-width: 1250px) {
  .content-box {
    padding: 40px 32px;
  }

  .content-box h2 {
    font-size: 3.2rem;
    margin-bottom: 20px;
  }

  .content-box p {
    font-size: 0.95rem;
    line-height: 1.6;
  }

  .btn {
    margin-top: 24px;
    padding: 12px 32px;
  }
}

/* 1100 */

@media (max-width: 1100px) {
  .content-box {
    padding: 30px 24px;
  }

  .content-box h2 {
    font-size: 2.8rem;
    margin-bottom: 18px;
  }

  .content-box p {
    font-size: 0.9rem;
    line-height: 1.55;
  }

  .btn {
    margin-top: 18px;
    padding: 10px 28px;
  }
}

/* 900 */

@media (max-width: 900px) {
  .content-box {
    flex: 0 0 300px;
    padding: 24px 20px;
  }

  .content-box h2 {
    font-size: 2.4rem;
    margin-bottom: 16px;
  }

  .content-box p {
    font-size: 0.88rem;
    line-height: 1.5;
  }

  .btn {
    margin-top: 16px;
    padding: 10px 24px;
  }

  .image-box {
    flex: 1;
  }
}

/* MOBILE */

@media (max-width: 700px) {
  .content-image,
  .content-image.right {
    flex-direction: column;
    padding: 50px 20px;
    box-sizing: border-box;
  }

  .content-box {
    width: calc(100% - 40px);
    max-width: 650px;

    box-sizing: border-box;

    margin-left: 0 !important;
    margin-right: 0 !important;
  }

  .image-box {
    width: calc(100% - 40px);
    max-width: 650px;

    box-sizing: border-box;

    border-radius: 30px;
    aspect-ratio: 1.5 / 1;

    order: -1;
  }
}
</style>