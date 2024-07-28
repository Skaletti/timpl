<template>
  <div v-if="props.visible" class="swen-modal" @click.self="closeDialog">
    <div class="swen-modal__body">
      <img src="@/assets/images/swen-modal-image.png" class="swen-modal__body-image">
      <div class="swen-modal__body-title">Profit goes to SWEN</div>
      <div class="swen-modal__body-description">By leaving a tip, you take care of nature</div>
      <a-button appearance="primary" class="swen-modal__body-button" @click="closeDialog">
        Learn more about SWEN
      </a-button>
      <a-button appearance="tertiary" class="swen-modal__body-button-close">
        <a-icon-template name="close-icon" width="24" height="24" @click="closeDialog" />
      </a-button>
    </div>

  </div>
</template>

<script setup lang="ts">
import { AButton } from "@/components";
import AIconTemplate from "@/components/atoms/AIconTemplate.vue";

type Props = {
  visible: boolean
}

const props = withDefaults(defineProps<Props>(), {
  visible: false,
})

const emit = defineEmits<{
  (e: 'close-dialog'): void
}>()

const closeDialog = (): void => {
  emit('close-dialog')
}
</script>

<style scoped lang="scss">
.swen-modal {
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  background-color: rgba(#314158, 0.4);

  &__body {
    position: relative;
    width: 320px;
    height: 352px;
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: var(--color-white);
    border-radius: 24px;
    padding: 12px;
  }

  &__body-image {
    width: 296px;
    height: 172px;
  }

  &__body-title {
    font-family: "Manrope", sans-serif;
    font-weight: 500;
    font-size: 18px;
    line-height: 24px;
    color: #262D35;
    width: 100%;
    max-width: 169px;
    margin-top: 16px;
    text-align: center;
  }

  &__body-description {
    font-family: "Manrope", sans-serif;
    font-weight: 400;
    font-size: 17px;
    line-height: 24px;
    color: #808191;
    width: 100%;
    max-width: 242px;
    margin-top: 8px;
    text-align: center;
  }

  &__body-button {
    margin-top: 16px;
  }

  &__body-button-close {
    position: absolute;
    width: 32px;
    height: 32px;
    top: 20px;
    right: 20px;
    border-radius: 30px;
    padding: 4px;
  }
}
</style>
