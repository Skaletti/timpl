<template>
  <div class="layout">
    <m-header class="header" />
    <m-marquee @click="dialogVisibleChange" />
    <m-person-slider :persons="person" class="mt-16" @update-person-name="handlePersonNameUpdate"/>
    <div class="container">
      <m-tips @update:tips="handleUpdateTips" class="mt-20" />
      <m-rating-selector class="mt-12" />
      <m-full-amount-payment :person="selectedPersonName" :isToggleActive="isFeesActive" class="mt-12" />
    </div>
  </div>
  <m-payment :tips-amount="tipsAmount" class="footer"/>
  <m-swen-modal :visible="isSwenModalVisible" @close-dialog="dialogVisibleChange" />
</template>

<script setup lang="ts">
import {
  MHeader,
  MMarquee,
  MTips,
  MPersonSlider,
  MPayment,
  MRatingSelector,
  MFullAmountPayment,
  MSwenModal
} from "@/components"

import { person } from "@/components/molecules/mocks"
import { ref } from "vue"

const tipsAmount = ref<number>(0)
const selectedPersonName = ref('')
const isFeesActive = ref(false)
const isSwenModalVisible = ref(false)

const handleUpdateTips = (value: number) => {
  tipsAmount.value = value
}

const handlePersonNameUpdate = (name: string) => {
  selectedPersonName.value = name
}

const dialogVisibleChange = (): void => {
  isSwenModalVisible.value = !isSwenModalVisible.value
}
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
