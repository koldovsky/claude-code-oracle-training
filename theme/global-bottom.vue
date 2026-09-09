<!-- Greenfield theme — persistent animated stage behind every slide. -->
<template>
  <div class="gf-stage-bg">
    <div class="gf-stage-aurora gf-aurora"></div>
    <div class="gf-stage-grid gf-grid"></div>
  </div>
</template>

<style>
.gf-stage-bg {
  position: absolute;
  inset: 0;
  overflow: hidden;
  pointer-events: none;
  background: radial-gradient(120% 90% at 50% -10%, #0E141A 0%, #07080B 60%);
  background-color: #07080B;
}
.gf-stage-grid {
  position: absolute;
  inset: 0;
  opacity: 0.4;
}
.gf-stage-aurora {
  position: absolute;
  inset: -20%;
  opacity: 0.45;
}
</style>
