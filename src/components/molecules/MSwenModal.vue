<template>
  <div class="swen-modal">
    <div class="swen-modal__body">
      <img src="@/assets/images/swen-modal-image.png" class="swen-modal__body-image">
      <div class="swen-modal__body-title">Profit goes to SWEN</div>
      <div class="swen-modal__body-description">By leaving a tip, you take care of nature</div>
      <a-button appearance="primary" class="swen-modal__body-button" />
    </div>

  </div>
</template>

<script setup lang="ts">

import { AButton } from "@/components";
</script>

<style scoped lang="scss">
.swen-modal {
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100vw;
  height: 100vh;
  background-color: rgba(#F7F9FC, 0.3);

  &__body {
    width: 320px;
    height: 352px;
  }
}
</style>
