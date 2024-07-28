<template>
  <div class="full-amount-payment">
    <div class="full-amount-payment__content">
      <div class="full-amount-payment__content-title">I want {{ props.person }} to receive <br> the full amount</div>
      <div class="full-amount-payment__content-description">
        You compensate service fee of 0.00€,<br> which will be applied to your payment.
      </div>
    </div>
    <a-toggle v-model="props.isToggleActive" />
  </div>
</template>

<script setup lang="ts">
import { AToggle } from "@/components";

type Props = {
  person: string
  isToggleActive: boolean
}

const props = defineProps<Props>()
</script>

<style scoped lang="scss">
.full-amount-payment {
  display: flex;
  align-items: center;
  background-color: var(--color-white);
  border-radius: 12px;
  padding: 16px;

  &__content {
    display: block;
    max-width: 241px;
    margin-right: 8px;
  }

  &__content-title {
    font-family: "Manrope", sans-serif;
    font-size: 14px;
    line-height: 20px;
    color: var(--color-black);
  }

  &__content-description {
    font-family: "Manrope", sans-serif;
    font-size: 12px;
    line-height: 14px;
    color: var(--color-grey);
    margin-top: 4px;
  }
}
</style>
