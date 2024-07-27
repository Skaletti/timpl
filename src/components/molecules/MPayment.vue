<template>
  <div class="payment container">
    <div class="payment__top">
      <div class="payment__top-total"> To pay {{props.tipsAmount}} €</div>
      <div class="payment__top-fees"> Service fees {{ fees }}€</div>
    </div>
    <div class="payment__separate"/>
    <div class="payment__content">
      <a-button appearance="primary" class="payment__content-button">
        Pay with
        <a-icon-template name="apple-pay-logo" width="47" height="24"/>
      </a-button>
      <a-button appearance="secondary" class="payment__content-button">
        Pay with debit card
      </a-button>
      <div class="payment__content-privacy">
        By clicking the button, you agree to our
        <a-link to="#">Terms of Use</a-link>
        and
        <a-link to="#">Privacy Policy</a-link>
        , and
        <a-link to="#">authorize payment</a-link>
        and
        <a-link to="#">data processing</a-link>
        .
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { AButton, ALink, AIconTemplate } from "@/components";
import { computed } from "vue";

type Props = {
  tipsAmount: number
}

const props = defineProps<Props>()

const fees = computed(() => {
  return (props.tipsAmount / 90).toFixed(2)
})
</script>

<style scoped lang="scss">
.payment {
  background-color: var(--color-white);
  border-radius: 20px 20px 0 0;
  padding: 24px 20px 11px;

  &__top {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  &__top-total {
    font-family: "Manrope", sans-serif;
    font-weight: 500;
    font-size: 15px;
    line-height: 24px;
    color: var(--color-black);
  }

  &__top-fees {
    font-family: "Manrope", sans-serif;
    font-weight: 500;
    font-size: 14px;
    line-height: 20px;
    color: var(--color-grey);
  }

  &__separate {
    width: 100%;
    height: 1px;
    background-color: #f3f3f3;
    margin-top: 12px;
  }

  &__content {
    display: block;
    margin-top: 12px;
  }

  &__content-button {
    &:nth-child(2) {
      margin-top: 8px;
    }
  }

  &__content-privacy {
    display: block;
    text-align: center;
    font-family: "Manrope", sans-serif;
    font-weight: 500;
    font-size: 11px;
    line-height: 15px;
    color: var(--color-grey);
    margin-top: 12px;
  }
}
</style>
