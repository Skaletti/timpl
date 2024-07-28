<template>
  <div class="rating-selector">
    <m-rating-bar title="Rate you experience" v-model:value="experienceRating" />
    <m-rating-bar class="mt-12" v-show="factor.ratingBarVisible" v-for="factor in factors" :title="factor.title" v-model:value="factor.rating" />

    <div v-if="isQuestionVisible" class="rating-selector__question">
      <div class="rating-selector__question-title">What did you like?</div>
      <div class="rating-selector__question-selectors">
        <div v-for="(factor, index) in factors"
             :key="index"
             class="rating-selector__question-selectors-item"
             @click="selectFactor(factor.title)"
             :class="{isActive: factor.ratingBarVisible}"
        >
          <div class="rating-selector__question-selectors-item__inner">
            <img :src="factor.img">
          </div>
          <span>{{ factor.title }}</span>
        </div>
      </div>
    </div>

    <div v-if="isQuestionVisible" class="rating-selector__feedback">
      <div class="rating-selector__feedback-title">Share your feedback</div>
      <textarea class="rating-selector__feedback-input" placeholder="Describe your own" />
    </div>
  </div>
</template>

<script setup lang="ts">
import { MRatingBar } from "@/components";
import { computed, ref } from "vue";
import type { factorsType } from "@/types";

const experienceRating = ref<number>(0)

const isQuestionVisible = computed(() => {
  return experienceRating.value > 1
})

const factors = ref<factorsType[]>([
  {
    rating: 0,
    title: "Service",
    img: "/src/assets/images/Service.png",
    ratingBarVisible: false
  },
  {
    rating: 0,
    title: "Cleanliness",
    img: "/src/assets/images/Cleanliness.png",
    ratingBarVisible: false
  },
  {
    rating: 0,
    title: "Atmosphere",
    img: "/src/assets/images/Atmosphere.png",
    ratingBarVisible: false
  },
  {
    rating: 0,
    title: "Food quality",
    img: "/src/assets/images/Food-quality.png",
    ratingBarVisible: false
  }
])

const selectFactor = (title: string) => {
  const factor = factors.value.find(f => f.title === title)

  if (factor) {
    factor.ratingBarVisible = !factor.ratingBarVisible
  }
}
</script>

<style scoped lang="scss">
.rating-selector {
  &__question {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 16px;
  }

  &__question-title {
    font-family: "Manrope", sans-serif;
    font-weight: 500;
    font-size: 15px;
    line-height: 24px;
  }

  &__question-selectors {
    display: flex;
    gap: 12px;
    margin-top: 12px;
  }

  &__question-selectors-item {
    display: block;
    max-width: 74px;

    &__inner {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 74px;
      height: 74px;
      border-radius: 12px;
      background-color: var(--color-white);
      background-image: url("@/assets/images/rating-selectors-background.png");

      img {
        width: 48px;
        height: 48px;
        object-fit: cover;
        object-position: center;
      }
    }

    span {
      display: block;
      font-family: "Manrope", sans-serif;
      font-size: 12px;
      line-height: 20px;
      color: var(--color-grey);
      margin-top: 4px;
      text-align: center;
    }

    &.isActive {
      .rating-selector__question-selectors-item__inner {
        background-color: var(--color-secondary);
      }

      span {
        color: var(--color-secondary);
      }
    }
  }

  &__feedback {
    display: block;
    margin-top: 16px;
  }

  &__feedback-title {
    text-align: center;
  }

  &__feedback-input {
    width: 100%;
    min-height: 104px;
    font-family: "Manrope", sans-serif;
    font-weight: 400;
    font-size: 17px;
    line-height: 24px;
    border: none;
    border-radius: 20px;
    background-color: var(--color-white);
    margin-top: 12px;
    padding: 20px;

    &:focus-visible {
      outline: 1px auto var(--color-secondary);
    }
  }
}
</style>
