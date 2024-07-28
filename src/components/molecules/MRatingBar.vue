<template>
  <div class="rating-bar">
    <div class="rating-bar__title">
      {{ props.title }}
    </div>
    <div class="rating-bar__selector">
      <span
          v-for="n in 5"
          :key="n"
          class="rating-bar__selector-star"
          :class="{ filled: n <= rating }"
          @click="setRating(n)"
      >
      <a-icon-template name="star" width="36" height="36"/>
    </span>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import AIconTemplate from "@/components/atoms/AIconTemplate.vue";

type Props = {
  value: number
  title: string
}

const props = defineProps<Props>()

const emits = defineEmits(['update:value'])

const rating = ref(props.value || 0)

const setRating = (n: number) => {
  rating.value = n
  emits('update:value', n)
}
</script>

<style scoped lang="scss">
.rating-bar {
  display: block;

  &__title {
    display: flex;
    align-items: center;
    white-space: nowrap;
    gap: 8px;
    color: var(--color-primary);

    &:before, &:after {
      content: '';
      width: 100%;
      height: 1px;
      background-color: var(--color-secondary);
    }
  }


  &__selector {
    display: flex;
    margin-top: 12px;
    padding: 20px 48px;
    justify-content: center;
    gap: 16px;
    background-color: var(--color-white);
    border-radius: 20px;
  }

  &__selector-star {
    font-size: 2rem;
    cursor: pointer;
    color: #CBD1D7;

    &.filled {
      color: var(--color-secondary);
    }
  }
}
</style>
