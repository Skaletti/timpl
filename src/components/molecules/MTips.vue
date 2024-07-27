<template>
  <div class="tips">
    <div class="tips__amount">
      <div class="tips__amount-title">Enter amount of tips</div>
      <div class="tips__amount-quantity">{{totalTips}}€</div>
    </div>
    <div class="tips__bottom">
      <a-button appearance="tertiary" class="tips__bottom-button f-grow" @click="selectTips(2)">2</a-button>
      <a-button appearance="tertiary" class="tips__bottom-button f-grow" @click="selectTips(5)">5</a-button>
      <a-button appearance="tertiary" class="tips__bottom-button f-grow" @click="selectTips(100)">100</a-button>
    </div>
  </div>
</template>

<script setup lang="ts">

import { ref } from "vue";
import { AButton } from "@/components";

const emit = defineEmits<{
  (event: 'update:tips', value: number): void;
}>();

const totalTips = ref<number>(0)
const selectTips = (count: number) => {
  totalTips.value = count
  emit('update:tips', count);
}
</script>

<style scoped lang="scss">
.tips {
  &__amount {
    width: 100%;
    height: 96px;
    display: block;
    background-color: var(--color-white);
    border-radius: 20px;
    padding: 12px;
  }

  &__amount-title {
    font-family: "Manrope", sans-serif;
    text-align: center;
    font-weight: 500;
    font-size: 15px;
    line-height: 24px;
    color: var(--color-black);
  }

  &__amount-quantity {
    font-family: "Manrope", sans-serif;
    text-align: center;
    font-weight: 700;
    font-size: 32px;
    line-height: 36px;
    opacity: 0.1;
    margin-top: 5px;
  }

  &__bottom {
    display: flex;
    gap: 4px;
    margin-top: 8px;
  }
}
</style>
