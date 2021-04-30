<template>
  <div class="about-container">
    <h1 class="themed-text">Built By.</h1>
    <p>Matthew Beckwith</p>
    <small>kodahScripts | <b class="sm-txt">&copy;</b>2021</small>
  </div>
</template>

<style scoped>
.about-container {
  display: flex;
  justify-content: center;
  flex-direction: column;
  text-align: center;
  margin-top: 220px;
  font-size: clamp(24px, 10vw, 48px);
  line-height: 70px;
}
.about-container > small {
  line-height: 13px;
  font-size: clamp(12px, 2vw, 24px);
}
.sm-txt {
  font-size: clamp(8px, 2vw, 14px);
}
</style>
