<!-- GfAgentNode — a single agent chip for orchestration diagrams. -->
<script setup>
import { computed } from "vue";
const props = defineProps({
  name: { type: String, default: "agent" },
  role: { type: String, default: "" },
  status: { type: String, default: "idle" },
  accent: { type: String, default: "violet" },
});
const accents = { green: "var(--green-400)", cyan: "var(--cyan-400)", violet: "var(--violet-400)", amber: "var(--amber-400)" };
const accentColor = computed(() => accents[props.accent] || accents.violet);
const statusMap = {
  idle:    { c: "var(--fg-3)",      label: "idle",    pulse: false },
  running: { c: accentColor.value,  label: "running", pulse: true },
  done:    { c: "var(--green-400)", label: "done",    pulse: false },
  blocked: { c: "var(--rose-400)",  label: "blocked", pulse: false },
};
const st = computed(() => statusMap[props.status] || statusMap.idle);
</script>

<template>
  <div class="gf-agent">
    <div class="gf-agent-ic" :style="{ color: accentColor, borderColor: accentColor }">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round">
        <rect x="4" y="7" width="16" height="12" rx="2.5" /><path d="M12 4v3M9 12h.01M15 12h.01" />
      </svg>
    </div>
    <div class="gf-agent-meta">
      <div class="gf-agent-name">{{ name }}</div>
      <div class="gf-agent-status">
        <span class="gf-agent-dot" :style="{ background: st.c, boxShadow: st.pulse ? '0 0 8px ' + st.c : 'none', animation: st.pulse ? 'gf-pulse 1.4s var(--ease-in-out) infinite' : 'none' }"></span>
        <span>{{ role || st.label }}</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.gf-agent { display: inline-flex; align-items: center; gap: 12px; padding: 12px 16px; border-radius: var(--radius-md); background: var(--ink-800); border: 1px solid var(--border-default); box-shadow: var(--inset-hairline); min-width: 190px; }
.gf-agent-ic { display: flex; align-items: center; justify-content: center; width: 38px; height: 38px; border-radius: var(--radius-sm); background: var(--ink-700); border: 1px solid; flex: none; }
.gf-agent-ic svg { width: 19px; height: 19px; }
.gf-agent-name { font-family: var(--font-mono); font-size: 14px; color: var(--fg-0); font-weight: 500; }
.gf-agent-status { display: flex; align-items: center; gap: 6px; margin-top: 3px; font-family: var(--font-mono); font-size: 11px; color: var(--fg-2); }
.gf-agent-dot { width: 7px; height: 7px; border-radius: 50%; flex: none; }
</style>
