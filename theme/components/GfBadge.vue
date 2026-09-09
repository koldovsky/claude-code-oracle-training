<!-- GfBadge — status / phase pill. -->
<script setup>
import { computed } from "vue";
const props = defineProps({
  tone: { type: String, default: "green" },
  variant: { type: String, default: "soft" },
  dot: { type: Boolean, default: false },
});
const tones = {
  green:  { fg: "var(--green-400)",  solidFg: "#042312", solidBg: "var(--green-500)",  tint: "var(--tint-green)",  line: "rgba(37,224,124,.45)" },
  cyan:   { fg: "var(--cyan-400)",   solidFg: "#04222B", solidBg: "var(--cyan-500)",   tint: "var(--tint-cyan)",   line: "rgba(31,192,236,.45)" },
  violet: { fg: "var(--violet-400)", solidFg: "#150A2E", solidBg: "var(--violet-500)", tint: "var(--tint-violet)", line: "rgba(139,92,246,.5)" },
  amber:  { fg: "var(--amber-400)",  solidFg: "#2A1B02", solidBg: "var(--amber-400)",  tint: "var(--tint-amber)",  line: "rgba(245,166,35,.5)" },
  rose:   { fg: "var(--rose-400)",   solidFg: "#2E0710", solidBg: "var(--rose-500)",   tint: "var(--tint-rose)",   line: "rgba(244,71,95,.5)" },
  neutral:{ fg: "var(--fg-1)",       solidFg: "#07080B", solidBg: "var(--fg-1)",       tint: "rgba(255,255,255,.06)", line: "var(--border-default)" },
};
const t = computed(() => tones[props.tone] || tones.green);
const style = computed(() => {
  if (props.variant === "solid") return { background: t.value.solidBg, color: t.value.solidFg, border: "1px solid transparent" };
  if (props.variant === "outline") return { background: "transparent", color: t.value.fg, border: `1px solid ${t.value.line}` };
  return { background: t.value.tint, color: t.value.fg, border: "1px solid transparent" };
});
</script>

<template>
  <span class="gf-badge" :style="style">
    <span v-if="dot" class="gf-badge-dot" :style="{ background: variant === 'solid' ? 'currentColor' : t.solidBg }"></span>
    <slot />
  </span>
</template>

<style scoped>
.gf-badge {
  display: inline-flex; align-items: center; gap: 6px;
  padding: 5px 12px;
  font-family: var(--font-mono); font-size: 13px; font-weight: 500;
  letter-spacing: 0.02em; line-height: 1; white-space: nowrap;
  border-radius: var(--radius-pill);
}
.gf-badge-dot { width: 6px; height: 6px; border-radius: 50%; flex: none; }
</style>
