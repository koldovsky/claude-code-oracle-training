<!-- Greenfield end / closing slide. -->
<script setup>
defineProps({
  brand: { type: String, default: "" },
});
</script>

<template>
  <div class="slidev-layout gf-end">
    <div class="gf-end-body">
      <slot />
    </div>
    <div class="gf-end-foot">
      <span>{{ brand }}</span>
    </div>
  </div>
</template>

<style>
.gf-end { display: flex; flex-direction: column; justify-content: center; }
.gf-end-body h1 { font-size: 84px; }
.gf-end-body p { font-size: 21px; max-width: 640px; margin-top: 1.1em; }
.gf-end-foot { position: absolute; left: var(--slide-pad-x); bottom: 48px; display: flex; align-items: center; gap: 12px; font-family: var(--font-mono); font-size: 13px; color: var(--fg-3); }
.gf-end-logo { height: 20px; width: auto; display: block; opacity: .9; }
</style>
