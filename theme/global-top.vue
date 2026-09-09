<!-- Greenfield theme — corner brand mark + page number, on top of slides.
     Hidden on cover and end layouts. -->
<template>
  <div
    v-if="show"
    class="gf-chrome"
  >
    <div class="gf-chrome-brand">
      <span class="gf-chrome-txt">Claude Code для Oracle-розробки</span>
    </div>
    <div class="gf-chrome-page">{{ pageStr }}</div>
  </div>
</template>

<script setup>
import { computed } from "vue";
import { useNav } from "@slidev/client";

const { currentLayout, currentPage, total } = useNav();
const hidden = ["cover", "end", "center", "section", "full"];
const show = computed(() => !hidden.includes(currentLayout.value));
const pageStr = computed(() => {
  const p = String(currentPage.value).padStart(2, "0");
  const t = String(total.value).padStart(2, "0");
  return `${p} / ${t}`;
});
</script>

<style>
.gf-chrome {
  position: absolute;
  left: 0; right: 0; bottom: 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 26px 40px;
  pointer-events: none;
  z-index: 20;
}
.gf-chrome-brand { display: flex; align-items: center; gap: 10px; }
.gf-chrome-logo { height: 17px; width: auto; display: block; opacity: .9; }
.gf-chrome-txt { font-family: var(--font-mono); font-size: 12px; letter-spacing: 0.04em; color: var(--fg-3); }
.gf-chrome-page { font-family: var(--font-mono); font-size: 12px; color: var(--fg-3); letter-spacing: 0.06em; }
</style>
