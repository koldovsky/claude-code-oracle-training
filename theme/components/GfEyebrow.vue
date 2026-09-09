<!-- GfEyebrow — mono uppercase kicker. Defaults to a leading "// ". -->
<script setup>
defineProps({ prefix: { type: String, default: "// " } });
</script>

<template>
  <div class="gf-eyebrow-c">{{ prefix }}<slot /></div>
</template>

<style scoped>
.gf-eyebrow-c {
  font-family: var(--font-mono);
  font-size: 14px;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--green-400);
  margin-bottom: 0.9em;
}
</style>
