<!-- Greenfield full-bleed layout: no padding, no chrome. For a slide that IS one image
     (partner / promo slides). Content is absolutely positioned over the whole canvas. -->
<template>
  <div class="slidev-layout gf-full">
    <slot />
  </div>
</template>

<style>
/* The slide root shrink-wraps its flow content in this theme, so pin the full-bleed
   layout to the page box (.slidev-page is 1280x720 and positioned). */
.gf-full { position: absolute; inset: 0; padding: 0; overflow: hidden; }
.gf-full .bleed { position: absolute; inset: 0; width: 100%; height: 100%; object-fit: cover; display: block; }
/* Invisible click targets placed over regions of the image (QR codes, e-mail lines). */
.gf-full .hotspot { position: absolute; display: block; border: none; border-radius: 10px; }
.gf-full .hotspot:hover { outline: 2px solid rgba(23, 143, 132, .55); outline-offset: 3px; }
</style>
