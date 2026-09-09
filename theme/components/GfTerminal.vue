<!-- GfTerminal — shell / code window. Pass :lines or use the default slot. -->
<script setup>
import { computed } from "vue";
const props = defineProps({
  title: { type: String, default: "agent — zsh" },
  accent: { type: String, default: "green" },
  glow: { type: Boolean, default: false },
  lines: { type: Array, default: null },
});
const accents = { green: "var(--green-400)", cyan: "var(--cyan-400)", violet: "var(--violet-400)", amber: "var(--amber-400)" };
const accentColor = computed(() => accents[props.accent] || accents.green);
function lineColor(ln) {
  if (ln.tone === "muted") return "var(--fg-3)";
  if (ln.tone === "accent") return accentColor.value;
  return "var(--fg-1)";
}
</script>

<template>
  <div class="gf-term" :style="{ boxShadow: glow ? 'var(--glow-green-soft), var(--shadow-lg)' : 'var(--shadow-lg)' }">
    <div class="gf-term-bar">
      <span class="gf-term-d" style="background:#FF5F57"></span>
      <span class="gf-term-d" style="background:#FEBC2E"></span>
      <span class="gf-term-d" style="background:#28C840"></span>
      <span class="gf-term-title">{{ title }}</span>
    </div>
    <div class="gf-term-body">
      <template v-if="lines">
        <div v-for="(ln, i) in lines" :key="i" class="gf-term-line" :style="{ color: lineColor(ln) }">
          <span v-if="ln.prompt !== false" class="gf-term-prompt" :style="{ color: accentColor }">{{ ln.prompt || "›" }} </span>{{ ln.text }}
        </div>
      </template>
      <slot v-else />
    </div>
  </div>
</template>

<style scoped>
.gf-term { border-radius: var(--radius-md); overflow: hidden; background: var(--ink-900); border: 1px solid var(--border-default); font-family: var(--font-mono); }
.gf-term-bar { display: flex; align-items: center; gap: 9px; padding: 12px 15px; background: var(--ink-850); border-bottom: 1px solid var(--border-subtle); }
.gf-term-d { width: 11px; height: 11px; border-radius: 50%; }
.gf-term-title { margin-left: 8px; font-size: 12px; color: var(--fg-3); }
.gf-term-body { padding: 18px 18px 20px; font-size: 14px; line-height: 1.8; color: var(--fg-1); }
.gf-term-line { white-space: pre-wrap; }
.gf-term-prompt { user-select: none; }
</style>
