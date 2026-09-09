<!-- Greenfield cover / title slide. Frontmatter: `brand` sets the top-left label. -->
<script setup>
defineProps({
  brand: { type: String, default: "" },
  tag: { type: String, default: "" },
});
</script>

<template>
  <div class="slidev-layout gf-cover">
    <div class="gf-cover-top">
      <div class="gf-cover-brand">
        <span class="gf-cover-brandtxt" v-html="brand"></span>
      </div>
      <span v-if="tag" class="gf-cover-tag">{{ tag }}</span>
    </div>
    <div class="gf-cover-body">
      <slot />
    </div>
  </div>
</template>

<style>
.gf-cover { display: flex; flex-direction: column; }
.gf-cover-top { display: flex; align-items: center; justify-content: space-between; }
.gf-cover-brand { display: flex; align-items: center; gap: 12px; font-family: var(--font-mono); font-size: 13px; color: var(--fg-1); letter-spacing: 0.04em; }
.gf-cover-logo { height: 30px; width: auto; display: block; }
.gf-cover-brandtxt { opacity: .85; }
.gf-cover-tag { font-family: var(--font-mono); font-size: 12px; letter-spacing: 0.16em; text-transform: uppercase; color: var(--green-400); border: 1px solid var(--border-accent); padding: 8px 14px; border-radius: var(--radius-pill); }
.gf-cover-body { margin-top: auto; }
.gf-cover-body h1 { font-size: 92px; }
.gf-cover-body p { font-size: 21px; max-width: 720px; margin-top: 1.1em; }
</style>
