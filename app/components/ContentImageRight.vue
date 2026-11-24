<template>
  <section class="content-image right">
    <div class="content-box">
      <h2>It's your<br>time now</h2>
      <p>
        Ready to reclaim control over your passions and ambitions?
        It's time to take the reins of your destiny and steer towards the life you've always dreamed of.
        Let's make strides in the right direction together. Don't wait for tomorrow; start today.
        Take that first step towards your goals and watch as your aspirations become your reality.
      </p>
      <button class="btn">Take Action</button>
    </div>

    <div class="image-box">
      <img src="/images/time-now.jpg" alt="It's your time now" />
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
}

.content-box {
  flex: 0 0 34%;
  background: #dde4d7;
  color: #1d382e;
  padding: 50px 40px;
  border-radius: 30px;
  margin-left: 0;
  margin-right: 30px;
}

.content-box h2 {
  font-size: 4rem;
  font-weight: 500;
  line-height: 0.9;
  margin: 0 0 25px;
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
  color: white;
  border: none;
  border-radius: 40px;
  cursor: pointer;
}

.btn:hover {
  background: #27483c;
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
  object-position: center;
  transition: transform 0.8s ease;
}

.image-box:hover img {
  transform: scale(1.08);
}
</style>