<!-- Greenfield center layout — fully centered content. -->
<template>
  <div class="slidev-layout gf-center">
    <div class="gf-center-inner">
      <slot />
    </div>
  </div>
</template>

<style>
.gf-center { display: flex; align-items: center; justify-content: center; text-align: center; }
.gf-center-inner { max-width: 1000px; }
.gf-center-inner p { margin-left: auto; margin-right: auto; max-width: 760px; }
</style>
