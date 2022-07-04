<template>
  <div class="body" @mousemove="createSpan($event)">

  </div>
</template>

<script setup lang="ts">
function createSpan(e: MouseEvent) {
  let particles = document.createElement('span');

  window.requestAnimationFrame(() => {
    let x = e.offsetX;
    let y = e.offsetY;
    particles.style.left = `${x}px`;
    particles.style.top = `${y}px`;

    let size = Math.random() * 8;
    particles.style.width = `${2 + size}px`;
    particles.style.height = `${2 + size}px`;

    let transformValue = Math.random() * 360;
    particles.style.transform = `rotate(${transformValue}deg)`;
  });

  (<HTMLElement>e.target).appendChild(particles);

  setTimeout(() => {
    particles.remove();
  }, 2000);
}
</script>

<style lang="scss" scoped>
* {
  margin: 0;
  padding: 0;
}

.body {
  min-height: 100vh;
  background: #111;
  position: relative;
  overflow: hidden;
}
</style>

<style lang="scss">
.body {

  >span {
    position: absolute;
    background: #f00;
    width: 10px;
    height: 10px;
    pointer-events: none;
    border-radius: 50%;

    &::before {
      content: "";
      position: absolute;
      width: 100%;
      height: 100%;
      background: #fff;
      border-radius: 50%;
      animation: moveParticles 2s linear infinite;
    }
  }
}

@keyframes moveParticles {
  0% {
    transform: translate(0);
  }

  100% {
    transform: translate(300px);
  }
}
</style>