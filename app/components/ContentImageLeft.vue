<template>
  <section class="content-image left">
    <div class="content-box">
      <h2>I'm<br>here..</h2>

      <p>
        Greetings, dear souls! I am Sylvan, your guide through the
        verdant realms of personal growth and empowerment.
        Nestled in the heart of nature, I draw inspiration from the
        wisdom of the forest to help you navigate the intricate paths
        of your own journey. With roots deeply anchored in resilience
        and branches reaching for the skies of limitless potential,
        I invite you to embrace change and flourish.
      </p>

      <button class="btn">
        Learn More
      </button>
    </div>

    <div class="image-box">
      <img
        src="/images/about.jpg"
        alt="Sylvan"
      />
    </div>
  </section>
</template>

<style scoped>
.content-image {
  display: flex;
  align-items: center;
  gap: 28px;
  background: #dde4d7;
  padding: 70px 0 70px 0;
  overflow: hidden;
}

.content-image.left {
  padding: 70px 0 70px 0;
}

.content-box {
  flex: 0 0 34%;
  background: #1d382e;
  color: white;
  padding: 50px 40px;
  border-radius: 30px;
  margin-right: 30px;
}

.content-image.left .content-box {
  margin-right: 0;
  margin-left: 30px;
}

.content-box h2 {
  font-size: 4rem;
  font-weight: 500;
  line-height: 0.9;
  margin: 0 0 25px;
  color: white;
}

.content-box p {
  font-size: 1rem;
  line-height: 1.7;
  opacity: 0.9;
  max-width: 420px;
}

.btn {
  margin-top: 30px;
  padding: 14px 40px;
  background: #e85a2a;
  color: #ffffff;
  border: none;
  border-radius: 40px;
  cursor: pointer;
}

.btn:hover {
  background: white;
}

.image-box {
  flex: 0 0 63%;
  aspect-ratio: 1.8 / 1;
  overflow: hidden;
  border-radius: 42px 0 0 42px;
}

.image-box img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  transition: transform 0.8s ease;
}

.image-box:hover img {
  transform: scale(1.08);
}
</style>