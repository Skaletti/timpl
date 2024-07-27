<template>
  <div class="marquee">
    <div class="marquee-content">
      <ul class="marquee-content__list">
        <li class="marquee-content__list-item">Part of the profit goes to sWen</li>
        <li class="marquee-content__list-item">
          <a-icon-template name="marquee-icon" width="19" height="24px" />
        </li>
        <li class="marquee-content__list-item">By leaving a tip, you take care of nature</li>
        <li class="marquee-content__list-item">
          <a-icon-template name="marquee-icon" width="19" height="24px" />
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup lang="ts">

import { AIconTemplate } from "@/components";
</script>

<style lang="scss" scoped>
.marquee {
  overflow: hidden;
  white-space: nowrap;
  box-sizing: border-box;
  background: linear-gradient(90deg, #F5CFC8, #DDFED5);
  max-width: 100vw;
}

.marquee-content {
  display: inline-block;
  padding: 12px 0 12px 100%;
  animation: marquee 18s linear infinite;

  &__list {
    display: flex;
    list-style: none;
    padding: 0;
    margin: 0;
  }

  &__list-item {
    font-family: "Montserrate", sans-serif;
    font-weight: 600;
    font-size: 16px;
    line-height: 20px;
    display: flex;
    align-items: center;
    margin-right: 8px;
    text-transform: uppercase;
  }
}

@keyframes marquee {
  0% { transform: translateX(0%); }
  100% { transform: translateX(-100%); }
}
</style>
