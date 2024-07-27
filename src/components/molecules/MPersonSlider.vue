<template>
  <swiper
      :slidesPerView="'auto'"
      :centeredSlides="true"
      :grabCursor="true"
      @slideChange="onSlideChange"
      :width="478"
      class="person-slider"
  >
    <swiper-slide
        v-for="(person, index) in props.persons"
        class="slider__slide"
        :class="{'person-slider__slide--active': activeIndex === index}">
      <img :src="person.image" class="person-slider__slide-image">
      <div class="person-slider__slide-content">
        <div class="person-slider__slide-content-name">
          {{ person.name }}
        </div>
        <span class="person-slider__slide-content-job">
          {{ person.job }}
        </span>
      </div>
    </swiper-slide>
  </swiper>
</template>

<script setup lang="ts">
import { Swiper, SwiperSlide } from 'swiper/vue'
import 'swiper/css'
import type {personType} from "@/types"
import { ref } from "vue";

type Props = {
  persons: personType[]
}

const props = defineProps<Props>()

const activeIndex = ref(0);

const onSlideChange = (swiper: any) => {
  activeIndex.value = swiper.activeIndex;
}
</script>

<style scoped lang="scss">
.person-slider {
  width: 100%;
  height: 92px;

  &__slide {
    display: flex;
    justify-content: center;
  }

  &__slide-content {
    display: none;
    flex-direction: column;
    justify-content: center;
  }

  &__slide-image {
    width: 106px;
    height: 66px;
    opacity: 0.2;
    border-radius: 1000px;
    object-fit: cover;
    object-position: center;
    margin-right: 12px;
  }

  &__slide-content-name {
    font-family: "Manrope", sans-serif;
    font-weight: 600;
    font-size: 22px;
    line-height: 24px;
    color: var(--color-primary);
  }

  &__slide-content-job {
    font-family: "Manrope", sans-serif;
    font-weight: 600;
    font-size: 16px;
    line-height: 20px;
    color: var(--color-secondary);
    margin-top: 4px;
  }

  .swiper-slide {
    width: 106px;
    margin-right: 36px;
  }

  .swiper-slide-active {
    width: 194px;
  }

  &__slide--active {
    display: flex;

    .person-slider__slide-content {
      display: flex;
      width: 100%;
    }

    .person-slider__slide-image {
      width: 92px;
      height: 92px;
      opacity: 1;
    }
  }
}
</style>
