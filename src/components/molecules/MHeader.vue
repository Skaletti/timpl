<template>
  <div class="header">
      <div class="header__logo">
        <a-icon-template name="logo" width="69" height="24"/>
      </div>

      <button class="header__lang-switch">
        <span>En</span>
        <a-icon-template name="chevron-bottom" width="10" height="6"/>
      </button>
    </div>
</template>

<script setup lang="ts">

import { AIconTemplate } from "@/components";
</script>

<style scoped lang="scss">
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: relative;
  width: 100vw;
  padding: 12px 20px;

  &__logo {
    display: flex;
    justify-content: center;
    width: 100%;
  }

  &__lang-switch {
    position: absolute;
    right: 20px;
    font-family: "Manrope", sans-serif;
    font-weight: 500;
    font-size: 16px;
    line-height: 24px;
    display: flex;
    align-items: center;
    column-gap: 4px;
    color: var(--color-primary);
    background-color: inherit;
    border: none;
  }

}
</style>
