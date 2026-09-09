<!-- GfStat — oversized metric for slides. -->
<script setup>
import { computed } from "vue";
const props = defineProps({
  value: { type: [String, Number], required: true },
  label: { type: String, default: "" },
  sublabel: { type: String, default: "" },
  accent: { type: String, default: "green" },
  gradient: { type: Boolean, default: false },
});
const accents = { green: "var(--green-400)", cyan: "var(--cyan-400)", violet: "var(--violet-400)", amber: "var(--amber-400)", plain: "var(--fg-0)" };
const valueStyle = computed(() =>
  props.gradient
    ? { background: "var(--grad-signal)", WebkitBackgroundClip: "text", backgroundClip: "text", color: "transparent" }
    : { color: accents[props.accent] || accents.green }
);
</script>

<template>
  <div class="gf-stat">
    <div class="gf-stat-val" :style="valueStyle">{{ value }}</div>
    <div v-if="label" class="gf-stat-label">{{ label }}</div>
    <div v-if="sublabel" class="gf-stat-sub">{{ sublabel }}</div>
  </div>
</template>

<style scoped>
.gf-stat-val { font-family: var(--font-display); font-weight: 700; font-size: 64px; line-height: 1; letter-spacing: -0.03em; }
.gf-stat-label { margin-top: 12px; font-size: 16px; color: var(--fg-1); font-weight: 500; }
.gf-stat-sub { margin-top: 4px; font-family: var(--font-mono); font-size: 12px; color: var(--fg-3); letter-spacing: 0.02em; }
</style>
