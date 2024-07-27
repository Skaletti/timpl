<template>
  <div class="rating-selector">
    <div v-for="(rating, index) in ratings" :key="index" class="rating-selector__block">
      <div class="rating-selector__block-separate">
        <div class="rating-selector__block-separate-line" />
        <div class="rating-selector__block-separate-title">{{ rating.category }}</div>
        <div class="rating-selector__block-separate-line" />
      </div>
      <MRatingBar v-model:value="rating.value" class="rating-selector__block-bar" />
      <div v-if="rating.value && !rating.submitted" class="rating-selector__question">
        <p class="rating-selector__question-title">What did you like?</p>
        <div class="rating-selector__question-block">
          <a-button
              appearance="tertiary"
              v-for="option in options"
              :key="option.name"
              class="rating-selector__question-block-button"
              :class="{ selected: rating.selectedOption === option.name }"
              :disabled="rating.selectedOption === option.name"
              @click="selectCategory(index, option.name)"
          >
            <div class="rating-selector__question-block-wrap"
                 :class="{ 'rating-selector__question-block-wrap--selected': rating.selectedOption === option.name }">
              <img :src="'/src/assets/images/' + option.name + '.png'" />
            </div>
            <span>{{ option.name }}</span>
          </a-button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { reactive } from 'vue'
import { MRatingBar, AButton } from "@/components";

const options = reactive([
  { name: 'Service', active: false },
  { name: 'Cleanliness', active: false },
  { name: 'Atmosphere', active: false },
  { name: 'Food-quality', active: false }
])

const ratings = reactive([
  { value: 0, category: 'Rate your experience', selectedOption: '', submitted: false }
])

const selectCategory = (index: number, optionName: string) => {
  ratings[index].selectedOption = optionName
  ratings[index].submitted = true
  if (ratings.length < 5) {
    ratings.push({ value: 0, category: optionName, selectedOption: '', submitted: false })
  }
}
</script>

<style scoped lang="scss">
.rating-selector {
  $--color-button-background: var(--color-white);
  $--color-button-background-selected: var(--color-secondary); // Новый цвет фона для выбранного состояния

  display: flex;
  flex-direction: column;
  gap: 16px;

  &__block {
    width: 100%;
  }

  &__block-bar {
    margin-top: 15px;
  }

  &__block-separate {
    display: flex;
    align-items: center;
    column-gap: 8px;
  }

  &__block-separate-line {
    display: flex;
    width: 100%;
    height: 1px;
    background-color: var(--color-secondary);
  }

  &__block-separate-title {
    display: flex;
    justify-content: center;
    width: fit-content;
    white-space: nowrap;
    font-family: $font-primary, sans-serif;
    font-weight: 500;
    font-size: 15px;
    line-height: 24px;
    color: var(--color-primary);
  }

  &__question {
    display: block;
  }

  &__question-title {
    font-family: $font-primary, sans-serif;
    font-weight: 500;
    font-size: 15px;
    line-height: 24px;
    color: var(--color-black);
    text-align: center;
  }

  &__question-block {
    display: grid;
    grid-template-columns: auto auto auto auto;
    max-width: 335px;
    gap: 12px;
  }

  &__question-block-button {
    display: block;
    width: 75px;
    height: 98px;
    font-family: "Manrope", sans-serif;
    font-size: 12px;
    line-height: 20px;
    color: #808191;
    padding: 0;
    background-color: inherit;

    &:active {
      color: var(--color-secondary);
    }

    img {
      width: 48px;
      height: 48px;
    }

    &:last-child {
      img {
        width: 59px;
        height: 58px;
      }
    }
  }

  &__question-block-wrap {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 75px;
    height: 75px;
    background-color: $--color-button-background;
    background-image: url("@/assets/images/rating-button-baclground.png");
    border-radius: 12px;

    &--selected {
      background-color: $--color-button-background-selected;
    }
  }
}
</style>

<!--<template>-->
<!--  <div class="rating-selector">-->
<!--    <div v-for="(rating, index) in ratings" :key="index" class="rating-selector__block">-->
<!--      <div class="rating-selector__block-separate">-->
<!--        <div class="rating-selector__block-separate-line" />-->
<!--        <div class="rating-selector__block-separate-title">{{ rating.category }}</div>-->
<!--        <div class="rating-selector__block-separate-line" />-->
<!--      </div>-->
<!--      <MRatingBar v-model:value="rating.value" class="rating-selector__block-bar" />-->
<!--      <div v-if="rating.value && !rating.submitted" class="rating-selector__question">-->
<!--        <p class="rating-selector__question-title">What did you like?</p>-->
<!--        <div class="rating-selector__question-block">-->
<!--          <a-button-->
<!--              appearance="tertiary"-->
<!--              v-for="option in options"-->
<!--              :key="option"-->
<!--              class="rating-selector__question-block-button"-->
<!--              :class="{ selected: rating.category === option }"-->
<!--              :disabled="rating.category === option"-->
<!--              @click="selectCategory(index, option)"-->
<!--          >-->
<!--            <div class="rating-selector__question-block-wrap">-->
<!--              <img :src="'/src/assets/images/' + option + '.png'" />-->
<!--            </div>-->

<!--            <span>{{ option }}</span>-->
<!--          </a-button>-->
<!--        </div>-->
<!--      </div>-->
<!--    </div>-->
<!--  </div>-->
<!--</template>-->

<!--<script setup lang="ts">-->
<!--import { reactive } from 'vue'-->
<!--import { MRatingBar, AButton } from "@/components";-->

<!--const options = ['Service', 'Cleanliness', 'Atmosphere', 'Food-quality']-->

<!--const ratings = reactive([-->
<!--  { value: 0, category: 'Rate your experience', submitted: false }-->
<!--])-->

<!--const selectCategory = (index: number, option: string) => {-->
<!--  ratings[index].submitted = true-->
<!--  if (ratings.length < 5) {-->
<!--    ratings.push({ value: 0, category: option, submitted: false })-->
<!--  }-->
<!--}-->
<!--</script>-->

<!--<style scoped lang="scss">-->
<!--.rating-selector {-->
<!--  $&#45;&#45;color-button-background: var(&#45;&#45;color-white);-->

<!--  display: flex;-->
<!--  flex-direction: column;-->
<!--  gap: 16px;-->

<!--  &__block {-->
<!--    width: 100%;-->
<!--  }-->

<!--  &__block-bar {-->
<!--    margin-top: 15px;-->
<!--  }-->

<!--  &__block-separate {-->
<!--    display: flex;-->
<!--    align-items: center;-->
<!--    column-gap: 8px;-->
<!--  }-->

<!--  &__block-separate-line {-->
<!--    display: flex;-->
<!--    width: 100%;-->
<!--    height: 1px;-->
<!--    background-color: var(&#45;&#45;color-secondary);-->
<!--  }-->

<!--  &__block-separate-title {-->
<!--    display: flex;-->
<!--    justify-content: center;-->
<!--    width: fit-content;-->
<!--    white-space: nowrap;-->
<!--    font-family: $font-primary, sans-serif;-->
<!--    font-weight: 500;-->
<!--    font-size: 15px;-->
<!--    line-height: 24px;-->
<!--    color: var(&#45;&#45;color-primary);-->
<!--  }-->

<!--  &__question {-->
<!--    display: block;-->
<!--  }-->

<!--  &__question-title {-->
<!--    font-family: $font-primary, sans-serif;-->
<!--    font-weight: 500;-->
<!--    font-size: 15px;-->
<!--    line-height: 24px;-->
<!--    color: var(&#45;&#45;color-black);-->
<!--    text-align: center;-->
<!--  }-->

<!--  &__question-block {-->
<!--    display: grid;-->
<!--    grid-template-columns: auto auto auto auto;-->
<!--    max-width: 335px;-->
<!--    gap: 12px;-->
<!--  }-->

<!--  &__question-block-button {-->
<!--    display: block;-->
<!--    width: 75px;-->
<!--    height: 98px;-->
<!--    font-family: "Manrope", sans-serif;-->
<!--    font-size: 12px;-->
<!--    line-height: 20px;-->
<!--    color: #808191;-->
<!--    padding: 0;-->
<!--    background-color: inherit;-->

<!--    &:active {-->
<!--      color: var(&#45;&#45;color-secondary);-->
<!--    }-->

<!--    img {-->
<!--      width: 48px;-->
<!--      height: 48px;-->

<!--    }-->

<!--    &:last-child {-->
<!--      img {-->
<!--        width: 59px;-->
<!--        height: 58px;-->
<!--      }-->
<!--    }-->
<!--    -->
<!--    &.selected {-->
<!--      $&#45;&#45;color-button-background: var(&#45;&#45;color-secondary);-->
<!--    }-->
<!--  }-->

<!--  &__question-block-wrap {-->
<!--    display: flex;-->
<!--    align-items: center;-->
<!--    justify-content: center;-->
<!--    width: 75px;-->
<!--    height: 75px;-->
<!--    background-color: $&#45;&#45;color-button-background;-->
<!--    background-image: url("@/assets/images/rating-button-baclground.png");-->
<!--    border-radius: 12px;-->
<!--  }-->
<!--}-->
<!--</style>-->
