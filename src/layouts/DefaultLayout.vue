<template>
  <div class="layout">
    <m-header class="header" />
    <m-marquee />
    <m-person-slider :persons="person" class="mt-16"/>
    <div class="container">
      <m-tips @update:tips="handleUpdateTips" class="mt-20" />
      <m-rating-selector class="mt-12" />
    </div>
  </div>
  <m-payment :tips-amount="tipsAmount" class="footer"/>
</template>

<script setup lang="ts">
import { MHeader, MMarquee, MTips, MPersonSlider, MPayment, MRatingSelector } from "@/components";
import { person } from "@/components/molecules/mocks";
import {ref} from "vue";

const tipsAmount = ref<number>(0);
const handleUpdateTips = (value: number) => {
  tipsAmount.value = value;
};
</script>

<style scoped>
.layout {
  display: flex;
  flex-direction: column;
  min-height: calc(100vh - 242px);
}

.footer {
  margin-top: 37px;
}
</style>
