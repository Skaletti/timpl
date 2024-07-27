<template>
  <div class="rating-bar">
    <span
        v-for="n in 5"
        :key="n"
        class="star"
        :class="{ filled: n <= rating }"
        @click="setRating(n)"
    >
      <a-icon-template name="star" width="36" height="36"/>
    </span>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import AIconTemplate from "@/components/atoms/AIconTemplate.vue";

const props = defineProps({
  value: Number
})

const emits = defineEmits(['update:value'])

const rating = ref(props.value || 0)

const setRating = (n: number) => {
  rating.value = n
  emits('update:value', n)
}
</script>

<style scoped>
.rating-bar {
  display: flex;
  padding: 20px 48px;
  justify-content: center;
  gap: 16px;
  background-color: var(--color-white);
  border-radius: 20px;
}
.star {
  font-size: 2rem;
  cursor: pointer;
  color: #CBD1D7;
}
.star.filled {
  color: var(--color-secondary);
}
</style>
