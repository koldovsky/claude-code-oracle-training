<!-- Greenfield default content layout. -->
<template>
  <div class="slidev-layout gf-default">
    <slot />
  </div>
</template>

<style>
.gf-default { display: flex; flex-direction: column; justify-content: center; }
.gf-default > h1:first-child,
.gf-default > h2:first-child { margin-top: 0; }
</style>
