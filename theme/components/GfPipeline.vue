<!-- GfPipeline — horizontal stage flow (SDD loop). -->
<script setup>
import { computed } from "vue";
const props = defineProps({
  steps: { type: Array, required: true },
  accent: { type: String, default: "green" },
  activeIndex: { type: Number, default: -1 },
});
const accents = { green: "var(--green-400)", cyan: "var(--cyan-400)", violet: "var(--violet-400)", amber: "var(--amber-400)" };
const accentColor = computed(() => accents[props.accent] || accents.green);
</script>

<template>
  <div class="gf-pipe">
    <template v-for="(step, i) in steps" :key="i">
      <div class="gf-pipe-step" :class="{ on: i <= activeIndex }">
        <div class="gf-pipe-num" :style="i <= activeIndex ? { background: accentColor, color: '#042312' } : {}">
          <span v-if="i < activeIndex">✓</span><span v-else>{{ i + 1 }}</span>
        </div>
        <div class="gf-pipe-label">{{ step.label }}</div>
        <div v-if="step.detail" class="gf-pipe-detail">{{ step.detail }}</div>
      </div>
      <div v-if="i < steps.length - 1" class="gf-pipe-arrow" :style="{ color: i < activeIndex ? accentColor : 'var(--fg-3)' }">
        <svg width="22" height="14" viewBox="0 0 22 14" fill="none"><path d="M1 7h18m0 0l-6-5m6 5l-6 5" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round" /></svg>
      </div>
    </template>
  </div>
</template>

<style scoped>
.gf-pipe { display: flex; align-items: stretch; }
.gf-pipe-step { flex: 1; min-width: 0; padding: 22px 20px; border-radius: var(--radius-md); background: var(--ink-850); border: 1px solid var(--border-subtle); }
.gf-pipe-step.on { background: var(--ink-800); border-color: var(--border-accent); box-shadow: var(--glow-green-soft); }
.gf-pipe-num { display: inline-flex; align-items: center; justify-content: center; width: 28px; height: 28px; border-radius: var(--radius-pill); font-family: var(--font-mono); font-size: 13px; font-weight: 600; margin-bottom: 14px; color: var(--fg-2); background: var(--ink-700); }
.gf-pipe-label { font-family: var(--font-display); font-size: 22px; font-weight: 600; color: var(--fg-0); letter-spacing: -0.01em; }
.gf-pipe-detail { margin-top: 6px; font-size: 14px; color: var(--fg-2); line-height: 1.4; }
.gf-pipe-arrow { display: flex; align-items: center; padding: 0 10px; flex: none; }
</style>
